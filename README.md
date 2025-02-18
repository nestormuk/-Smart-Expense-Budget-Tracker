# Smart Expense & Budget Tracker for Students
📌 Description
A personal finance management app that helps students track their daily expenses, manage budgets, and save money efficiently.
🛠️ Core Features
Expense Logging & Categorization – Manually enter and categorize expenses.
Budget Setting & Alerts – Users define a monthly budget and get notifications when overspending.
Savings Goals & Reminders – Helps users track savings goals.
Simple Reports & Graphs – Visual representation of spending habits.
Offline Storage – All transactions are stored locally for offline access.


Here's a Postman documentation for testing each of your APIs based

1. UserController
POST /api/users/register
Description: Registers a new user and sends an OTP to their email.
Request Body:
 {
    "name": "John Doe",
    "email": "john.doe@example.com"
}


Response:
 {
    "message": "OTP sent to email"
}


POST /api/users/verify
Description: Verifies the user's OTP for registration.
Request Body:
 {
    "email": "john.doe@example.com",
    "otp": "123456"
}


Response:
 {
    "message": "User verified successfully"
}
 Or if invalid OTP:
 {
    "message": "Invalid OTP"
}



2. SavingsGoalController
POST /api/goals/create
Description: Creates a new savings goal for a user.
Request Body:
 {
    "email": "john.doe@example.com",
    "name": "Vacation Fund",
    "targetAmount": 5000.00
}


Response:
 {
    "id": 1,
    "name": "Vacation Fund",
    "targetAmount": 5000.00,
    "savedAmount": 0.00,
    "user": {
        "id": 1,
        "name": "John Doe",
        "email": "john.doe@example.com"
    }
}


GET /api/goals/{email}
Description: Fetches all savings goals of a user.
Response (for a user with existing goals):
 [
    {
        "id": 1,
        "name": "Vacation Fund",
        "targetAmount": 5000.00,
        "savedAmount": 100.00
    }
]
 Or if no goals:
 []


PUT /api/goals/update/{id}
Description: Updates an existing savings goal.
Request Body:
 {
    "name": "Updated Vacation Fund",
    "targetAmount": 6000.00,
    "savedAmount": 500.00
}


Response:
 {
    "id": 1,
    "name": "Updated Vacation Fund",
    "targetAmount": 6000.00,
    "savedAmount": 500.00
}


DELETE /api/goals/delete/{id}
Description: Deletes a savings goal.
Response:
 {
    "message": "Goal deleted successfully"
}
 Or if goal not found:
 {
    "message": "Goal not found"
}



3. ExpenseController
POST /api/expenses/add
Description: Adds a new expense for a user.
Request Body:
 {
    "email": "john.doe@example.com",
    "category": "Food",
    "amount": 50.00,
    "description": "Lunch"
}


Response:
 {
    "id": 1,
    "category": "Food",
    "amount": 50.00,
    "description": "Lunch",
    "date": "2025-02-18T00:00:00.000+00:00",
    "user": {
        "id": 1,
        "name": "John Doe",
        "email": "john.doe@example.com"
    }
}


GET /api/expenses/{email}
Description: Retrieves all expenses of a user.
Response (for a user with expenses):
 [
    {
        "id": 1,
        "category": "Food",
        "amount": 50.00,
        "description": "Lunch",
        "date": "2025-02-18T00:00:00.000+00:00"
    }
]
 Or if no expenses:
 []


PUT /api/expenses/update/{id}
Description: Updates an existing expense.
Request Body:
 {
    "category": "Food",
    "amount": 60.00,
    "description": "Dinner",
    "date": "2025-02-18T00:00:00.000+00:00"
}


Response:
 {
    "id": 1,
    "category": "Food",
    "amount": 60.00,
    "description": "Dinner",
    "date": "2025-02-18T00:00:00.000+00:00"
}


DELETE /api/expenses/delete/{id}
Description: Deletes an expense.
Response:
 {
    "message": "Expense deleted successfully"
}
 Or if expense not found:
 {
    "message": "Expense not found"
}



4. BudgetController
POST /api/budget/set
Description: Sets a budget for a user.
Request Body:
 {
    "email": "john.doe@example.com",
    "amount": 1000.00,
    "period": "monthly"
}


Response:
 {
    "id": 1,
    "amount": 1000.00,
    "period": "monthly",
    "user": {
        "id": 1,
        "name": "John Doe",
        "email": "john.doe@example.com"
    }
}


GET /api/budget/get/{email}
Description: Retrieves the budget for a user.
Response:
 {
    "id": 1,
    "amount": 1000.00,
    "period": "monthly"
}
 Or if no budget:
 "User not found"


PUT /api/budget/update/{email}
Description: Updates the budget for a user.
Request Body:
 {
    "amount": 1200.00,
    "period": "monthly"
}


Response:
 {
    "id": 1,
    "amount": 1200.00,
    "period": "monthly"
}


DELETE /api/budget/delete/{email}
Description: Deletes a user's budget.
Response:
 {
    "message": "Budget deleted successfully"
}



Postman Testing Steps
Register User:


Test POST /api/users/register to create a new user.
Follow by POST /api/users/verify to verify the OTP.
Create, View, Update, Delete Goals:


Test POST /api/goals/create to create a savings goal.
Test GET /api/goals/{email} to view goals.
Test PUT /api/goals/update/{id} to update a goal.
Test DELETE /api/goals/delete/{id} to delete a goal.
Manage Expenses:


Test POST /api/expenses/add to add a new expense.
Test GET /api/expenses/{email} to view expenses.
Test PUT /api/expenses/update/{id} to update an expense.
Test DELETE /api/expenses/delete/{id} to delete an expense.
Manage Budget:


Test POST /api/budget/set to set a budget.
Test GET /api/budget/get/{email} to view budget.
Test PUT /api/budget/update/{email} to update the budget.
Test DELETE /api/budget/delete/{email} to delete a budget.

By following this, you can fully test the CRUD operations of each controller via Postman. Each API endpoint has been named and documented with expected input/output. 


