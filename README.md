# airbnb-clone-project
# Airbnb Clone Project

## 📌 Project Overview

This project is a simplified clone of the Airbnb platform. It replicates the core functionality of Airbnb, allowing users to list, discover, and book accommodations. It is built as a collaborative full-stack web application to demonstrate practical skills in software engineering, system design, and team collaboration.

### 🎯 Project Goals

- Build a scalable full-stack web application
- Practice clean architecture and RESTful API design
- Learn about secure user authentication and authorization
- Understand and apply relational database modeling
- Gain experience in continuous integration and deployment (CI/CD)

### 💻 Tech Stack

- **Frontend**: HTML, CSS, JavaScript, Bootstrap
- **Backend**: Python, Django
- **Database**: PostgreSQL
- **Version Control**: Git & GitHub
- **CI/CD**: GitHub Actions, Docker (for deployment)

---

## 👥 Team Roles

### 1. **Frontend Developer**
Designs and implements the user-facing interface using web technologies. Ensures responsiveness, accessibility, and usability across devices.

### 2. **Backend Developer**
Responsible for creating APIs, business logic, and integration with databases. Manages authentication, authorization, and data validation.

### 3. **Database Administrator (DBA)**
Designs and maintains the database schema, relationships, and performance optimization. Ensures backup and migration strategy.

### 4. **DevOps Engineer**
Sets up deployment workflows and CI/CD pipelines. Monitors application environments, handles Docker containers, and ensures uptime.

### 5. **Project Manager**
Oversees task allocation, timeline planning, and inter-team communication. Tracks progress and ensures timely delivery.

### 6. **QA Tester**
Tests application features for functionality, performance, and security. Writes automated tests and conducts manual review cycles.

---

## 📚 Technology Stack

| Technology     | Purpose |
|----------------|---------|
| **Django**     | Backend web framework used for building REST APIs, authentication, and business logic. |
| **PostgreSQL** | Relational database to store structured data (users, listings, bookings, etc.). |
| **HTML/CSS**   | Used to create and style the structure and layout of the web interface. |
| **JavaScript** | Adds interactivity to web pages, such as form handling and dynamic content updates. |
| **Bootstrap**  | Speeds up UI development by providing pre-built responsive design components. |
| **Docker**     | Containerization tool to ensure consistent environments during development and deployment. |
| **GitHub Actions** | Automates testing, building, and deploying the application. |
| **Git & GitHub** | For version control, team collaboration, and open-source hosting. |

---

## 🧩 Database Design

### Key Entities and Fields

#### 1. **User**
- `id` (Primary Key)
- `username`
- `email`
- `password`
- `user_type` (Host/Guest)

#### 2. **Property**
- `id` (Primary Key)
- `host_id` (Foreign Key to User)
- `title`
- `location`
- `price_per_night`

#### 3. **Booking**
- `id` (Primary Key)
- `property_id` (FK to Property)
- `guest_id` (FK to User)
- `check_in`
- `check_out`

#### 4. **Review**
- `id` (Primary Key)
- `property_id` (FK to Property)
- `user_id` (FK to User)
- `rating`
- `comment`

#### 5. **Payment**
- `id` (Primary Key)
- `booking_id` (FK to Booking)
- `amount`
- `payment_status`
- `payment_date`

### Entity Relationships

- A **User** can act as a host (owning properties) or a guest (making bookings).
- A **Property** is owned by one user and can receive multiple bookings and reviews.
- A **Booking** links a guest to a property and includes check-in/out details.
- A **Review** is left by a user after a completed stay at a property.
- A **Payment** is tied to a specific booking and records transaction details.

---

## 🧱 Feature Breakdown

### 1. **User Management**
Users can register as either guests or hosts. Authentication, login, password reset, and profile management features are included.

### 2. **Property Management**
Hosts can create, update, and delete property listings with relevant details like location, images, and pricing.

### 3. **Booking System**
Guests can view available properties and create bookings. The system ensures availability, prevents conflicts, and tracks reservation status.

### 4. **Review System**
Guests can leave reviews and ratings for properties they’ve stayed at. These reviews help improve host quality and guide future users.

### 5. **Payment Integration**
Handles secure payments for bookings. Tracks payment status and integrates with a gateway like Stripe or PayPal.

### 6. **Admin Dashboard**
Admins can view, approve, or delete listings and manage user activity across the platform.

---

## 🔒 API Security

### Key Measures

1. **Authentication**
   - JSON Web Tokens (JWT) are used to authenticate users and maintain sessions securely.

2. **Authorization**
   - Access control mechanisms ensure that users only access resources they are permitted to.

3. **Rate Limiting**
   - Prevents abuse or DoS attacks by limiting how frequently APIs can be called.

4. **Input Validation**
   - All inputs are validated and sanitized to prevent common attacks like SQL injection and XSS.

5. **HTTPS**
   - All communications are encrypted to protect user credentials and transaction data.

### Importance

- **User Protection**: Sensitive user data like emails and passwords must be protected.
- **Platform Trust**: Maintaining user trust requires strong privacy and data protection.
- **Secure Transactions**: Booking and payment data must be safe from tampering or interception.

---

## 🔁 CI/CD Pipeline

### What is CI/CD?

CI/CD stands for **Continuous Integration** and **Continuous Deployment/Delivery**. It is a modern development practice that automates the process of building, testing, and deploying code.

### Why It Matters:

- Reduces manual errors during deployment
- Encourages frequent integration of code changes
- Detects bugs early in the development lifecycle

### Tools Used:

- **GitHub Actions** – Automates test suites and deployment steps
- **Docker** – Ensures a consistent development and production environment
- **Heroku / Render / AWS** – For hosting and running the deployed application

---

## ✅ Manual Review Checklist

- [x] Project repository is **public** and named `airbnb-clone-project`
- [x] `README.md` is complete with all required sections:
  - Project Overview
  - Team Roles
  - Technology Stack
  - Database Design
  - Feature Breakdown
  - API Security
  - CI/CD Pipeline
- [x] All changes committed and pushed to GitHub
- [x] Proper Markdown formatting used for readability and structure
- [x] Project ready for team collaboration and instructor review




