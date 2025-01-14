# Bank Database Management System

This project demonstrates the implementation of a relational database management system (RDBMS) for a bank. The database includes tables for managing bank branches, employees, customers, accounts, loans, transactions, and their relationships. Additionally, views are created to provide summarized information for easy retrieval.

## Database Structure

### 1. Tables
#### a. `BankBranch`
- **Fields:**
  - `BranchID` (Primary Key): Unique identifier for the branch.
  - `BranchName`: Name of the bank branch.
  - `BranchCity`: City where the branch is located.
  - `BranchCountry`: Country where the branch is located.
  - `BranchPhone`: Contact number of the branch.
  - `ManagerID`: ID of the branch manager.

#### b. `Employee`
- **Fields:**
  - `EmployeeID` (Primary Key): Unique identifier for the employee.
  - `EmployeeName`: Name of the employee.
  - `EmployeeAddress`: Address of the employee.
  - `EmployeePhone`: Contact number of the employee.
  - `EmployeeEmail`: Email address of the employee.
  - `BranchID` (Foreign Key): Links the employee to a branch.
  - `DepartmentID`: Department where the employee works.

#### c. `Department`
- **Fields:**
  - `DepartmentID` (Primary Key): Unique identifier for the department.
  - `DepartmentName`: Name of the department.
  - `HeadOfDepartment`: ID of the department head.
  - `Designation`: Job designation of the head.

#### d. `Customer`
- **Fields:**
  - `CustomerID` (Primary Key): Unique identifier for the customer.
  - `CustomerName`: Name of the customer.
  - `CustomerAddress`: Address of the customer.
  - `CustomerPhone`: Contact number of the customer.
  - `CustomerEmail`: Email address of the customer.
  - `BranchID` (Foreign Key): Links the customer to a branch.
  - `AccountNumber`: Linked account number.

#### e. `Account`
- **Fields:**
  - `AccountNumber` (Primary Key): Unique identifier for the account.
  - `BranchID` (Foreign Key): Links the account to a branch.
  - `CustomerID` (Foreign Key): Links the account to a customer.
  - `AccountType`: Type of account (e.g., Savings, Checking).
  - `Balance`: Current balance in the account.
  - `InterestRate`: Applicable interest rate.
  - `AccountStatus`: Current status of the account (e.g., Active).

#### f. `Loan`
- **Fields:**
  - `LoanID` (Primary Key): Unique identifier for the loan.
  - `AccountNumber` (Foreign Key): Linked account number.
  - `InterestRate`: Interest rate of the loan.
  - `Duration`: Duration of the loan in months.
  - `StartDate`: Starting date of the loan.
  - `DueAmount`: Total due amount for the loan.

#### g. `Transaction`
- **Fields:**
  - `TransactionID` (Primary Key): Unique identifier for the transaction.
  - `AccountNumber` (Foreign Key): Linked account number.
  - `DateTime`: Timestamp of the transaction.
  - `EmployeeID` (Foreign Key): Employee involved in the transaction.
  - `CreditDeposit`: Amount credited or debited in the transaction.
  - `LoanID` (Foreign Key): Linked loan ID, if applicable.
  - `TransactionType`: Type of transaction (e.g., Deposit, Withdrawal).

### 2. Views

#### a. `AccountDetailsview`
- Combines data from `Account`, `Customer`, and `BankBranch` to provide a comprehensive account overview.

#### b. `EmployeeDetailsview`
- Combines data from `Employee` and `BankBranch` to provide details about employees and their branch affiliations.

#### c. `TransactionDetailsview`
- Combines data from `Transaction` and `Customer` to summarize transaction details for customers.

## Sample Queries
### Retrieve Transaction Details:
```sql
SELECT * FROM TransactionDetailsview;
```

### View Account Details:
```sql
SELECT * FROM AccountDetailsview;
```

### View Employee Details:
```sql
SELECT * FROM EmployeeDetailsview;
```

## Features
1. **Referential Integrity:**
   - Foreign keys ensure proper relationships between tables.
2. **Data Normalization:**
   - Structured to avoid data redundancy.
3. **Views:**
   - Simplify data access and enhance readability.
4. **Comprehensive Entities:**
   - Includes essential details for managing a banking system.

## How to Use
1. **Create Database and Tables:**
   Execute the SQL script to create the database schema and tables.
2. **Insert Sample Data:**
   Use the provided `INSERT` statements to populate tables with sample data.
3. **Run Queries:**
   Execute queries to fetch desired information using the views and tables.

## Future Enhancements
1. Include additional modules like credit card management and investments.
2. Implement triggers and stored procedures for automated operations.
3. Enhance security with encryption for sensitive data like account details and customer information.
