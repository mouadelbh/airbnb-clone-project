# Airbnb Clone Project (FullStack App)

This project is a full-stack clone of the popular accommodation booking platform AirBnB. The goal is to build a functional web application that allows users to browse property listings, view detailed property information, and complete bookings. The project will cover frontend development, backend APIs, database design, and deployment.

### 🎯 Feature Breakdown

  **1. User Management**
Users can register, log in, and manage their profiles securely. Authentication ensures only authorized access to personal data and actions.

  **2. Property Management**
Hosts can create, update, and delete property listings, providing detailed information and setting rental prices. This enables a flexible and dynamic hosting experience.

  **3. Booking System**
Users can book properties for specific dates, with automatic conflict checks and reservation status tracking. This forms the core transactional functionality of the platform.

  **4. Payment Processing**
Secure payment handling allows users to pay for bookings using integrated payment services. Each payment is tied to a specific booking to ensure traceability.

  **5. Review System**
Guests can leave reviews and ratings for properties after their stay. This promotes transparency and trust among users and hosts.

  **6. Asynchronous Tasks**
Tasks such as email confirmations or notifications are handled in the background using Celery, improving performance and user experience.

  **7. API Security**
Security measures like token-based authentication and input validation are implemented to protect user data and prevent unauthorized access.

  **8. CI/CD Integration**
Automated testing and deployment pipelines ensure code quality and speed up the development process with consistent builds and rollouts.

### 👥 Team Roles

- **Backend Developer** : Handles API development, server logic, and integration.
- **Database Administrator** : Designs, optimizes, and maintains the relational database.
- **DevOps Engineer** : Sets up CI/CD pipelines, manages Docker environments, and handles deployment infrastructure.
- **QA Engineer** : Ensures the backend functionalities are thoroughly tested and meet quality standards.

### ⚙️ Technology Stack

- **Django** : A high-level Python web framework used for building the RESTful API.
- **Django REST Framework** : Django REST Framework: Provides tools for creating and managing RESTful APIs.
- **PostgreSQL** : A powerful relational database used for data storage.
- **GraphQL** : Allows for flexible and efficient querying of data.
- **Celery** : Handles asynchronous tasks such as sending notifications or processing payments.
- **Redis** : Used for caching and session management.
- **Docker** : Containerization tool for consistent development and deployment environments.
- **CI/CD Pipelines** : Automated pipelines for testing and deploying code changes.

### 🗄️ Database Design

#### Objective
Understand how the database will be structured to support the core functionality of the Airbnb Clone application.

#### Key Entities and Fields

**1. User**
- `id`: Unique user identifier (primary key).
- `name`: Full name of the user.
- `email`: Unique email used for login.
- `password`: Hashed password for authentication.
- `created_at`: Timestamp of account creation.

**2. Property**
- `id`: Unique property identifier (primary key).
- `owner_id`: References the User who owns the property.
- `title`: Name or title of the property.
- `description`: Detailed information about the listing.
- `price_per_night`: Rental price per night.

**3. Booking**
- `id`: Unique booking identifier (primary key).
- `user_id`: References the User who made the booking.
- `property_id`: References the Property being booked.
- `check_in`: Start date of the booking.
- `check_out`: End date of the booking.

**4. Payment**
- `id`: Unique payment identifier (primary key).
- `booking_id`: References the related Booking.
- `amount`: Total payment amount.
- `status`: Payment status (e.g., paid, pending, failed).
- `payment_date`: Date and time of the payment.

**5. Review**
- `id`: Unique review identifier (primary key).
- `user_id`: References the User who submitted the review.
- `property_id`: References the Property being reviewed.
- `rating`: Numeric rating (e.g., 1–5).
- `comment`: Text content of the review.

#### Entity Relationships

- A **User** can own many **Properties**.
- A **User** can make many **Bookings**.
- A **Property** belongs to one **User** and can have many **Bookings** and **Reviews**.
- A **Booking** is linked to one **User**, one **Property**, and one **Payment**.
- A **Payment** is made for one **Booking**.
- A **Review** is submitted by a **User** and linked to one **Property**.

### 🔐 API Security

To ensure data protection and system integrity, several backend security measures are implemented:

- **Authentication**: Verifies the identity of users using secure methods such as token-based authentication (e.g., JWT). This ensures that only registered users can access protected endpoints.
- **Authorization**: Restricts access to certain actions based on user roles (e.g., only property owners can edit their listings). This prevents unauthorized operations.
- **Input Validation & Sanitization**: Prevents injection attacks (SQL, XSS) by ensuring user input is clean and controlled.
- **Rate Limiting**: Limits the number of requests per user/IP to protect against brute-force attacks and API abuse.
- **HTTPS Enforcement**: Ensures all data is encrypted during transmission.

#### 🔐 Why Security Matters:
- **User Data Protection**: Personal info like emails and passwords must remain confidential.
- **Payment Integrity**: Transactions must be securely processed and verified to prevent fraud.
- **Platform Trust**: Strong security helps build trust among users and hosts.

### 🔁 CI/CD Pipeline

**Continuous Integration (CI)** and **Continuous Deployment (CD)** are essential for efficient software development and delivery. CI/CD pipelines automatically test, build, and deploy code changes, reducing human error and speeding up the release cycle.

#### 🚧 Benefits:
- Ensures that code is thoroughly tested before deployment.
- Automates repetitive tasks like running unit tests, linting, and pushing updates to staging/production environments.
- Promotes faster feedback and collaboration within the team.

#### 🛠️ Tools That Could Be Used:
- **GitHub Actions**: Automates workflows for testing and deploying the project.
- **Docker**: Ensures consistency across development and production environments.
- **Celery & Redis**: Background task processing within the pipeline.

CI/CD integration is especially important in this project to support collaborative development, frequent updates, and a smooth deployment process.

