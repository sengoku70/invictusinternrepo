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

**How to reproduce:** Filter or sort the expenses (for example, search for an expense or view sorted expenses), then click "Delete" or edit the amount on an expense.

**What is wrong:** Deleting or updating an expense relied on the list position number (array index) instead of its unique ID. As a result, deleting an item in a sorted or filtered list would delete a completely different expense, and updating the reducer to use IDs caused delete to stop working because the ID was not being passed properly from the app component.

**What I changed:**
1. Updated `store.js` reducer so `DELETE_EXPENSE` and `UPDATE_EXPENSE` find and modify items by `id`.
2. Updated `App.jsx` to pass `id` to `DELETE_EXPENSE` and `UPDATE_EXPENSE` action dispatches.
3. Updated `ExpenseList.jsx` to pass `expense.id` to the delete and update action handlers.

---
