# Overview: airbnb-clone-project 
The backend for the Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments. This backend will support various functionalities required to mimic the core features of Airbnb, ensuring a smooth experience for users and hosts.

## Project Goals
1. User Management: Implement a secure system for user registration, authentication, and profile management.
2. Property Management: Develop features for property listing creation, updates, and retrieval.
3. Booking System: Create a booking mechanism for users to reserve properties and manage booking details.
4. Payment Processing: Integrate a payment system to handle transactions and record payment details.
5. Review System: Allow users to leave reviews and ratings for properties.
6. Data Optimization: Ensure efficient data retrieval and storage through database optimizations.

## Team Roles
1. Backend Developer: Responsible for implementing API endpoints, database schemas, and business logic.
2. Database Administrator: Manages database design, indexing, and optimizations.
3. DevOps Engineer: Handles deployment, monitoring, and scaling of the backend services.
4. QA Engineer: Ensures the backend functionalities are thoroughly tested and meet quality standards.

## Technology Stack
- Django: A high-level Python web framework used for building the RESTful API.
- Django REST Framework: Provides tools for creating and managing RESTful APIs.
- PostgreSQL: A powerful relational database used for data storage.
- GraphQL: Allows for flexible and efficient querying of data.
- Celery: For handling asynchronous tasks such as sending notifications or processing payments.
- Redis: Used for caching and session management.
- Docker: Containerization tool for consistent development and deployment environments.
- CI/CD Pipelines: Automated pipelines for testing and deploying code changes.

## Database Design
### 1. Users
Represents both guests and hosts on the platform.
- `id`: Unique identifier for each user.
- `name`: Full name of the user.
- `email`: Email address (used for login).
- `password_hash`: Hashed password for authentication.
- `is_host`: Boolean flag to determine if the user is a host.

### 2. Properties
Listings created by hosts for rental.
- `id`: Unique identifier for each property.
- `title`: Name/title of the property.
- `description`: Detailed information about the property.
- `location`: Geographical location of the property.
- `host_id`: Foreign key referencing the User who owns the property.

### 3. Bookings
Records of reservations made by users for properties.
- `id`: Unique identifier for each booking.
- `property_id`: Foreign key referencing the Property.
- `user_id`: Foreign key referencing the User (guest).
- `check_in`: Start date of the booking.
- `check_out`: End date of the booking.

### 4. Reviews
Feedback and ratings submitted by guests.
- `id`: Unique identifier for each review.
- `user_id`: Foreign key referencing the User who wrote the review.
- `property_id`: Foreign key referencing the Property being reviewed.
- `rating`: Numerical rating (e.g., 1–5).
- `comment`: Text content of the review.

### 5. Payments
Handles financial transactions associated with bookings.
- `id`: Unique identifier for each payment.
- `booking_id`: Foreign key referencing the Booking.
- `amount`: Total amount paid.
- `payment_status`: Enum indicating status (e.g., pending, completed).
- `payment_date`: Timestamp of when the payment was processed.

---

### Entity Relationships

- A **User** can list multiple **Properties** (1-to-many).
- A **Property** can have multiple **Bookings** (1-to-many).
- A **Booking** belongs to one **Property** and one **User** (many-to-1).
- A **Property** can receive multiple **Reviews** (1-to-many).
- A **Review** is written by a **User** for a **Property** (many-to-1).
- A **Booking** has one associated **Payment** (1-to-1).


## Feature Breakdown
1. API Documentation
OpenAPI Standard: The backend APIs are documented using the OpenAPI standard to ensure clarity and ease of integration.
Django REST Framework: Provides a comprehensive RESTful API for handling CRUD operations on user and property data.
GraphQL: Offers a flexible and efficient query mechanism for interacting with the backend.
2. User Authentication
Endpoints: /users/, /users/{user_id}/
Features: Register new users, authenticate, and manage user profiles.
3. Property Management
Endpoints: /properties/, /properties/{property_id}/
Features: Create, update, retrieve, and delete property listings.
4. Booking System
Endpoints: /bookings/, /bookings/{booking_id}/
Features: Make, update, and manage bookings, including check-in and check-out details.
5. Payment Processing
Endpoints: /payments/
Features: Handle payment transactions related to bookings.
6. Review System
Endpoints: /reviews/, /reviews/{review_id}/
Features: Post and manage reviews for properties.
7. Database Optimizations
Indexing: Implement indexes for fast retrieval of frequently accessed data.
Caching: Use caching strategies to reduce database load and improve performance.


