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
