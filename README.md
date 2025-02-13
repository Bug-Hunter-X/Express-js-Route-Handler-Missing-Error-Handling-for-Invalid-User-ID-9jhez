# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  Specifically, the `/users/:id` route fails to handle cases where the `id` parameter is not a valid integer.

## Bug

The `bug.js` file contains the buggy code.  The `req.params.id` is directly parsed as an integer without any validation or error handling. If `req.params.id` is not a valid integer (e.g., a string, or contains non-numeric characters), `parseInt(userId)` returns `NaN`, causing the `.find()` method to return `undefined`, leading to no error being thrown.  This could crash the application, display unexpected errors, or silently fail, making debugging more difficult.

## Solution

The `bugSolution.js` file provides a corrected version of the code.  It includes checks to ensure the `userId` is a valid integer before attempting to find the user.  It also handles the case where a user with the given ID is not found, returning a 404 status code.

## How to Run

1. Clone this repository.
2. Run `npm install express` to install the Express.js dependency.
3. Run `node bug.js` to execute the buggy code (and then test with an invalid ID).
4. Run `node bugSolution.js` to execute the corrected code (and then test with an invalid ID).