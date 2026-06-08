# Employee Management System (EMS)

A desktop application built with **C# Windows Forms** and **SQL Server** to automate core HR tasks for small to medium‑sized organisations. The system manages employee records, attendance, leave requests, salary processing, performance reviews, and user accounts with role‑based access (Admin / User).

## Features

- **User Login & Authentication** – Secure login with username/password. Role (Admin/User) is stored in session.
- **Employee Management** – Add, update, delete, and search employees. Only Admin can edit; regular users can only view.
- **Attendance Tracking** – Mark daily attendance (Present/Absent). Duplicate entries are prevented. Admin can delete records.
- **Leave Management** – Employees submit leave requests (Annual, Sick, Casual, Unpaid). Admin can approve, reject, or delete requests.
- **Salary Processing** – Automatically calculate monthly net salary based on basic salary and leave days. View payslips. Admin only.
- **Performance Reviews** – Record reviews with rating (1–5), reviewer, comments, and review period. Admin can add/update/delete; users view only.
- **User Management** – Admin can add, update, or delete user accounts and assign roles. Non‑admin users cannot access this form.
- **Password Change** – Any logged‑in user can change their own password (old password verification, confirmation match, app restart).

## Technologies Used

- **Front‑end:** C# .NET Framework 4.7.2, Windows Forms
- **Back‑end:** Microsoft SQL Server
- **Data Access:** ADO.NET TableAdapters (typed DataSet)
- **IDE:** Visual Studio 2019 / 2022

## Database Schema

The database consists of six tables:

- `Employees` – employee personal and salary details
- `Attendance` – daily attendance records (unique constraint on EmployeeID + AttendanceDate)
- `LeaveRequests` – leave applications with status (Pending, Approved, Rejected)
- `Salary` – monthly salary calculations
- `PerformanceReviews` – employee performance reviews
- `Users` – login credentials and roles (Admin / User)

All foreign keys have `ON DELETE CASCADE`.

## Setup Instructions

### Prerequisites

- Windows 7/10/11
- .NET Framework 4.7.2 or higher
- SQL Server (Express, Developer, or LocalDB)
- Visual Studio (optional, for editing source code)

### Step 1: Create the Database

1. Open **SQL Server Management Studio** (or Visual Studio’s SQL Server Object Explorer).
2. Run the script `EMSDB.sql` (included in the repository). This will:
   - Create the `EMSDB` database.
   - Create all six tables.
   - Insert sample data (6 employees, attendance, leave requests, salary records, reviews, and 3 users).

### Step 2: Configure the Connection String

- Open `App.config` (or `Settings.settings`).
- Ensure the `Data Source` matches your SQL Server instance (e.g., `localhost`, `(localdb)\MSSQLLocalDB`, or `YOUR_PC_NAME\SQLEXPRESS`).

### Step 3: Build and Run

- Open the solution file (`EMS.sln`) in Visual Studio.
- Build the solution (Ctrl+Shift+B).
- Run the application (F5).

### Default Login Credentials

| Username | Password | Role    |
|----------|----------|---------|
| admin    | admin123 | Admin   |
| user1    | pass123  | User    |
| manager  | manager456 | Admin |

## Project Structure
