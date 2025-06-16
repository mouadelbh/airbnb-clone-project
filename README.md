# Airbnb Clone Project (FullStack App)

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
