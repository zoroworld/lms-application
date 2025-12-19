# LMS Admin Panel

A Learning Management System (LMS) Admin Panel built using **Laravel 10** and **PHP 8.1**, designed to manage users, courses, enrollments, and progress tracking with secure authentication and real-time notifications.

---

## Project Overview

The LMS Admin Panel enables administrators to:

* Manage users, roles, and permissions
* Create and manage courses and lessons
* Track student progress in real time
* Send push notifications using OneSignal
* Secure the system using authentication and role-based access control

---

## Admin Credentials (Demo)

* **Email:** `admin@gmail.com`
* **Password:** `1234`

---

## Tech Stack

* **Backend:** Laravel 10
* **Language:** PHP 8.1
* **Database:** MySQL (`lms.sql`)
* **Authentication:** Laravel Auth / JWT (if enabled)
* **Notifications:** OneSignal Web SDK
* **Containerization:** Docker & Docker Compose

---

## Database

* Database file: `lms.sql`
* Import the database before running the application.

---

## Notifications

Push notifications are implemented using **OneSignal Web SDK**.

Documentation: [https://documentation.onesignal.com/docs/web-sdk-setup](https://documentation.onesignal.com/docs/web-sdk-setup)

Used for:

* Course updates
* Enrollment notifications
* Admin announcements

---

## Docker Setup

### Update / Reinstall Containers

```bash
docker-compose down
docker-compose build
docker-compose up -d
```

### Start Laravel in Docker

```bash
docker-compose up
```

### Stop Laravel Containers

```bash
docker-compose down
```

### View Running Containers

```bash
docker ps
```

---

## API Design

### Authentication APIs

| Method | Endpoint     | Description                |
| ------ | ------------ | -------------------------- |
| POST   | /api/login   | User login                 |
| POST   | /api/logout  | User logout                |
| GET    | /api/profile | Get logged-in user details |

---

### User Management

| Method | Endpoint        | Description      |
| ------ | --------------- | ---------------- |
| GET    | /api/users      | List all users   |
| POST   | /api/users      | Create new user  |
| GET    | /api/users/{id} | Get user details |
| PUT    | /api/users/{id} | Update user      |
| DELETE | /api/users/{id} | Delete user      |

---

### Course Management

| Method | Endpoint          | Description    |
| ------ | ----------------- | -------------- |
| GET    | /api/courses      | List courses   |
| POST   | /api/courses      | Create course  |
| GET    | /api/courses/{id} | Course details |
| PUT    | /api/courses/{id} | Update course  |
| DELETE | /api/courses/{id} | Delete course  |

---

### Enrollment & Progress

| Method | Endpoint               | Description           |
| ------ | ---------------------- | --------------------- |
| POST   | /api/enroll            | Enroll user in course |
| GET    | /api/progress/{userId} | Get course progress   |
| PUT    | /api/progress/update   | Update progress       |

---

## Core Classes & Models

```
User
Course
Lesson
Enrollment
Progress
Role
Notification
```

---

## Model Relationships

### User Model

* User hasMany Enrollments
* User belongsToMany Courses
* User hasMany Progress
* User belongsTo Role

### Course Model

* Course hasMany Lessons
* Course belongsToMany Users
* Course hasMany Enrollments

### Lesson Model

* Lesson belongsTo Course

### Enrollment Model

* Enrollment belongsTo User
* Enrollment belongsTo Course

### Progress Model

* Progress belongsTo User
* Progress belongsTo Course

### Role Model

* Role hasMany Users

---

## Testing

* Unit testing for models and services
* API testing for authentication and course management
* Integration testing for enrollment and progress tracking
* Manual UI testing for admin workflows

---

## Features Summary

* Secure authentication with role-based access
* RESTful API architecture
* Real-time progress tracking
* Push notifications via OneSignal
* Dockerized environment for easy setup
* Scalable and modular Laravel codebase

---

## Future Enhancements

* Student dashboard
* Certificate generation
* Advanced analytics
* Email notifications

