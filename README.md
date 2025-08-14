# 📝 To-do List System

**Project Start Date:** 14 August 2025  
**Author:** [Your Name]

---

## 🎯 Goal

Build a simple internal To-do List system for task assignment and tracking with multi-role access control. The system must be easy to use and mobile-friendly.

---

## 👥 User Roles & Permissions

| Role      | Permissions                                                                 |
|-----------|------------------------------------------------------------------------------|
| CEO       | Full access: assign tasks, override approvals, manage users                 |
| CTO/CIO/COO | First-level task approval, view and comment on tasks                       |
| Manager   | Assign tasks to Staff, receive tasks from CxO, mark progress                |
| Staff     | Create tasks, accept/decline assigned tasks, update progress                |

---

## 📋 Core Features

### 🧑‍💼 User Management (Admin Only)
- Create/edit/delete users
- Assign roles to users

### ✅ Task Management
- Create task (title, description, assigned user, etc.)
- Start and end date
- Status: Pending, Approved, Rejected
- Progress: Not Started, In Progress, Done
- Notes
- Problem logs

### 🔁 Task Approval Workflow
- Task created by Staff or Manager → requires CTO/CIO/COO approval
- CEO can override or fast-track approvals

### 📊 Dashboard
- Task list view with:
  - Filters (status, user, role)
  - Search by keyword
  - Color codes for task status

---

## 🗂️ Data Model

### User
- `id` (int)
- `name` (string)
- `email` (string)
- `password` (hashed)
- `role` (enum: CEO, CTO, CIO, COO, Manager, Staff)

### Task
- `id` (int)
- `title` (string)
- `description` (text)
- `assigned_to` (foreign key: user_id)
- `assigned_by` (foreign key: user_id)
- `start_date` (date)
- `end_date` (date)
- `progress` (enum: Not Started, In Progress, Done)
- `status` (enum: Pending, Approved, Rejected)
- `notes` (text, nullable)
- `problems` (text, nullable)
- `created_at` / `updated_at` (timestamp)

---

## 🖼️ UI Requirements

- Responsive design using Bootstrap 5.3
- Clean dashboard with task cards or rows
- Modal forms for add/edit
- Filters and search bar
- Date picker UI for selecting start/end dates

---

## 📁 Project Structure

```

/app
  /Controllers
  /Models
  /Views (optional PHP view logic)
/routes
  web.php
/public
  index.php (front controller)
  /assets (Bootstrap, JS)
/config
  config.php
/storage
  /logs
.env
composer.json

```

---

## 📌 Non-Functional Requirements

- **Security**: Passwords hashed with bcrypt; `.env` never exposed
- **Database**: MariaDB 11.4 with PDO + prepared statements
- **Code Style**: PHP 8.3, strict types, PSR-4 autoloading
- **No Frameworks**: Pure PHP only, MVC pattern

---

## ✅ MVP Checklist

- [ ] User login and role-based access
- [ ] Task CRUD
- [ ] Task approval workflow
- [ ] Dashboard with filters
- [ ] Mobile responsive UI

---

## 📅 Suggested Timeline

| Week | Milestone                           |
|------|-------------------------------------|
| 1    | User system, login, roles           |
| 2    | Task model and CRUD                 |
| 3    | Approval flow and dashboard filters |
| 4    | UI polishing, bug fixes             |