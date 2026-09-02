# Bugs found

Add one section per issue. Bug 1 is filled in to show the format — fix it, then write what you changed. Copy the blank template for the rest.

Keep this file in the repo and **commit it** with your fixes.

---

## Bug 1

**How to reproduce:** Open the app. The expense list says “Newest first”. The first row is Wine (7 Mar). Board game (15 Mar) is further down.

**What is wrong:** The list is showing oldest expenses first. Newest should be at the top.

**What I changed:**

1.in the format.js returning the format as a Date object so it can be mathematically subtracted and processed
    2. in the expanse list the sorted array of dates as b.date -> a.date so the latest date is at the top

## Bug 2

**How to reproduce:** Filter or search for an expense, or keep them sorted, and click the "Delete" button or edit the amount on any expense.

**What is wrong:** The app was tracking expenses by their array position (index) rather than their unique ID. When the list was filtered or sorted, deleting an item deleted a completely different expense from the group.

**What I changed:**
1. In `ExpenseList.jsx`, used `expense.id` as the unique key and passed `expense.id` to the delete and update actions.
2. In `App.jsx`, passed `id` in the dispatch calls for `DELETE_EXPENSE` and `UPDATE_EXPENSE`.
3. In `store.js`, updated the reducer to delete and update items matching `e.id === action.id` instead of using array indexes.

---

## Bug 3

**How to reproduce:** In the "Filter" card, select any person from the "Paid by" dropdown (e.g. Aisha Khan).

**What is wrong:** The app shows "No expenses match these filters." for any person selected, even though there are expenses paid by them. The dropdown returns a string ID (e.g. `"1"`) while the expense stores a number (`1`), causing the strict check `e.paidBy !== paidBy` to fail.

**What I changed:**
In `App.jsx`, updated the filter condition to compare values as strings (`String(e.paidBy) !== String(paidBy)`) so that selecting a person correctly displays their expenses.

---

## Bug 4

**How to reproduce:** Enter a description and an amount in the "Add expense" form and click "Save expense".

**What is wrong:** After the expense is added, the description and amount input fields remain filled with the old values instead of resetting, making it easy to accidentally submit duplicate entries.

**What I changed:**
In AddExpenseForm.jsx, I added setDescription("") and setAmount("") inside the form's submi` handler so the input boxes automatically clear after successfully saving an expense.

---
