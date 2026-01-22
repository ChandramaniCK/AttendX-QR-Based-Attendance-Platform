QR-Based Attendance System
System Design Document

1️⃣ Problem Statement
Traditional attendance systems are time-consuming, error-prone, and allow proxy attendance. The goal of this system is to automate attendance using QR codes, ensure security, and provide real-time reporting for educational institutions.

2️⃣ Objectives
Automate attendance using QR scanning
Prevent duplicate and proxy attendance
Provide role-based access (Admin, Faculty, Student)
Enable real-time attendance tracking and reports

3️⃣ Functional Requirements
Admin
Manage users (students, faculty)
Create and manage classes
View global attendance reports
Faculty
Generate time-bound QR codes
View class-wise attendance
Download attendance reports
Student
Scan QR code to mark attendance
View personal attendance history

4️⃣ Non-Functional Requirements
Security: QR expiry, duplicate scan prevention
Performance: Handle concurrent scans
Scalability: Multiple classes & sessions
Reliability: Accurate attendance logging
Usability: Simple UI for quick scanning

5️⃣ Tech Stack
Frontend: React, HTML, CSS, Bootstrap
Backend: Spring Boot, Java
Database: MySQL
Security: JWT Authentication
Utilities: QR Code Generator Library

6️⃣ High Level Design (HLD)
Architecture Style
3-Tier Architecture
Client (React UI)
      ↓
Backend (Spring Boot REST APIs)
      ↓
Database (MySQL)
Flow Overview
Faculty generates QR code
Student scans QR
Backend validates QR
Attendance stored in DB
Reports generated

7️⃣ Low Level Design (LLD)
Database Entities
User
Class
QR Session
Attendance
Key APIs
Method	Endpoint	Description
POST	/auth/login	User authentication
POST	/qr/generate	Generate QR
POST	/attendance/mark	Mark attendance
GET	/attendance/student	Student history
GET	/attendance/class	Class report

8️⃣ Security Design
JWT-based authentication
QR token expiry using timestamps
Unique constraint (student + session)
Role-based API access

9️⃣ Assumptions & Constraints
Students must scan within class time window
Internet connection required
QR codes are regenerated per session

🔟 Future Enhancements
Mobile app support
Face recognition integration
Location-based validation
Push notifications

📦 Module Division (8 Modules)

🖥️ Frontend Modules (3)

1️⃣ Authentication & Role Module
Login UI
Role-based routing
JWT token handling

2️⃣ Faculty & Admin Dashboard Module
QR generation UI
Attendance view
Class management screens

3️⃣ Student Attendance Module
QR scan page
Attendance history
Profile view

⚙️ Backend Modules (5)

4️⃣ Authentication & Authorization Module
Login APIs
JWT token generation
Role validation

5️⃣ User & Class Management Module
CRUD for students & faculty
Class creation & assignment

6️⃣ QR Session Management Module
QR token generation
Session expiry handling
Active QR validation

7️⃣ Attendance Processing Module
QR scan validation
Duplicate scan prevention
Attendance persistence

8️⃣ Reporting & Audit Module
Attendance reports
Date & class filters
CSV export
Logs for admin review
