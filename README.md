EMS (Employee Management System) - README
Overview
EMS (Employee Management System) is a Windows Forms desktop application built with C# and .NET Framework 4.7.2. It provides comprehensive employee management functionality including attendance tracking, leave requests, salary processing, performance reviews, and user management.

System Requirements
Operating System: Windows 7 or later

.NET Framework: Version 4.7.2 or higher

Database: Microsoft SQL Server (local or remote)

IDE: Visual Studio 2017 or later (for development)

Database Setup
Step 1: Create the Database
Open SQL Server Management Studio (SSMS) or your preferred SQL client

Run the EMSDB.sql script located in the project folder

The script will:

Create a database named EMSDB

Create all required tables (Employees, Attendance, LeaveRequests, Salary, PerformanceReviews, Users)

Insert sample data for testing

Step 2: Update Connection String
The application uses Windows Authentication by default. The connection string is configured in:

App.config

EMS.exe.config

Default connection string:

xml
Data Source=localhost;Initial Catalog=EMSDB;Integrated Security=True;Encrypt=False;TrustServerCertificate=True
If you need to change the connection:

Change localhost to your SQL Server instance name

Or switch to SQL Server Authentication by modifying the connection string

Login Credentials
Role	Username	Password
Admin	admin	admin123
User	user1	pass123
Admin	manager	manager456
Features
1. Login System
Secure authentication with role-based access

Clear form and exit options

2. Dashboard (Main Form)
Central navigation hub

Welcome message with logged-in user info

Role-based button visibility (Admin sees all features)

3. Employee Management (Admin only)
Add, update, delete employee records

Search employees by name, position, email, or phone

View employee list in data grid

Fields: First Name, Last Name, Position, Email, Phone, Hire Date, Basic Salary

4. Attendance Management
All users: Mark attendance (Present/Absent/HalfDay/Leave)

Admin only: Delete attendance records

View attendance history in data grid

Duplicate check prevents multiple entries for same employee on same date

5. Leave Request Management
All users: Submit leave requests (Annual, Sick, Casual, Unpaid)

Admin only: Approve, reject, or delete leave requests

Track request status (Pending/Approved/Rejected)

6. Salary Processing (Admin only)
Process monthly salaries based on attendance

Automatic calculation:

Deductions based on leave days

Daily wage = Basic Salary / Total Days

Net Salary = Basic Salary - Deductions + Bonus

View payslip for any salary record

Delete salary records

Prevents duplicate processing for same month

7. Performance Reviews (Admin only)
Add, update, delete employee performance reviews

Rating system (1-5 stars)

Review period tracking

Comments section for detailed feedback

8. User Management (Admin only)
Add, update, delete system users

Assign roles (Admin/User)

Change passwords

Cannot delete own account

9. Password Change
Any logged-in user can change their password

Requires old password verification

Password confirmation check

Role-Based Access Control
Feature	Admin	Regular User
View Employees	✓	✓
Add/Update/Delete Employees	✓	✗
Mark Attendance	✓	✓
Delete Attendance Records	✓	✗
Submit Leave Requests	✓	✓
Approve/Reject Leave Requests	✓	✗
Process Salaries	✓	✗
View Payslips	✓	✓
Manage Performance Reviews	✓	✗
Manage Users	✓	✗
Change Password	✓	✓
Project Structure
text
EMS/
├── Login.cs                 # Authentication form
├── Main.cs                  # Dashboard with navigation
├── Employee.cs              # Employee CRUD operations
├── Attendance.cs            # Attendance marking and viewing
├── LeaveRequest.cs          # Leave request submission and management
├── Salary.cs                # Salary processing and payslips
├── PerformanceReview.cs     # Performance review management
├── UserManagemnt.cs         # User account management (Admin only)
├── PasswordChange.cs        # Password change functionality
├── Session.cs               # Static class for user session data
├── Database.cs              # Database connection helper
├── EMSDBDataSet.xsd         # Typed DataSet for database operations
├── EMSDB.sql                # Database creation script
└── App.config               # Application configuration
How to Run the Application
From Visual Studio:
Open the solution file (EMS.sln)

Ensure the database is set up and running

Press F5 or click Start Debugging

From Compiled Executable:
Navigate to bin/Debug/ or bin/Release/

Run EMS.exe

Ensure the database server is accessible

Troubleshooting
Database Connection Error
Verify SQL Server is running

Check the connection string in App.config

Ensure Windows Authentication is enabled or update to SQL Authentication

Login Failed
Confirm username and password from the sample data

Check that the Users table contains data

Duplicate Key Errors
Attendance: Cannot mark attendance for same employee on same date twice

Salary: Cannot process same month twice for an employee

Development Notes
The application uses Typed DataSets for database operations

All forms inherit from Form and use Windows Forms controls

Session management is handled via static Session class

Error handling includes try-catch blocks with user-friendly messages

Future Enhancements
Export reports to Excel/PDF

Email notifications for leave approvals

Dashboard with charts and analytics

Backup and restore functionality

Audit trail for all transactions

Developed with C# and .NET Framework 4.7.2
