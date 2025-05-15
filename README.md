# Airbnb Clone Backend

## Overview

This project is a backend system for an Airbnb Clone, designed to support a wide range of functionalities such as user management, property listings, bookings, payments, and reviews. Built for scalability and performance, this backend provides RESTful and GraphQL APIs to ensure smooth and flexible client interaction.

## Project Goals

- **User Management**: Secure registration, login, and user profile handling.
- **Property Management**: Create, update, and manage property listings.
- **Booking System**: Enable users to make and manage reservations.
- **Payment Processing**: Handle payments and record transactions.
- **Review System**: Allow users to leave and manage reviews.
- **Data Optimization**: Ensure efficient data handling with indexing and caching.

## Technology Stack

- **Django**: High-level Python web framework.
- **Django REST Framework**: For building RESTful APIs.
- **PostgreSQL**: Relational database for data storage.
- **GraphQL**: Flexible data querying and mutation.
- **Celery**: Asynchronous task processing.
- **Redis**: Caching and session management.
- **Docker**: Containerization for consistent environments.
- **CI/CD Pipelines**: Automated testing and deployment.

## Team Roles

### Backend Developer
Responsible for implementing the core application logic, designing and building API endpoints, creating serializers, and integrating services such as authentication, bookings, and payments. Ensures the backend code is clean, maintainable, and scalable.

### Database Administrator
Designs the database schema and relationships between entities. Handles data migrations, indexing, backups, and performance optimizations to ensure fast and reliable data access.

### DevOps Engineer
Manages the infrastructure for development, staging, and production environments. Handles containerization using Docker, sets up CI/CD pipelines, monitors deployments, and ensures the application scales efficiently.

### QA Engineer
Writes and runs test cases to validate backend features. Ensures that all APIs work as expected and meet defined requirements. Reports bugs and works closely with developers to maintain a high-quality codebase.


## Database Design

The backend is structured around several core entities that represent the essential components of the Airbnb platform. Each entity includes key fields and is related to others to maintain data integrity and functionality.

### Users
Represents individuals who can register on the platform as either guests or hosts.
- `id`: Unique identifier for each user.
- `name`: Full name of the user.
- `email`: Unique email address for login and communication.
- `password_hash`: Securely stored password.
- `is_host`: Boolean flag indicating if the user is a property host.

**Relationships:**
- A user can own multiple properties.
- A user can make multiple bookings.
- A user can leave multiple reviews.

### Properties
Represents listings available for booking on the platform.
- `id`: Unique identifier for each property.
- `title`: Title or name of the property.
- `description`: Detailed description of the property.
- `location`: Address or coordinates of the property.
- `price_per_night`: Cost per night to book the property.

**Relationships:**
- Each property is owned by one user (host).
- A property can have multiple bookings.
- A property can have multiple reviews.

### Bookings
Represents reservations made by users for specific properties.
- `id`: Unique identifier for each booking.
- `user_id`: The user who made the booking.
- `property_id`: The property being booked.
- `start_date`: Booking check-in date.
- `end_date`: Booking check-out date.

**Relationships:**
- Each booking is linked to one user.
- Each booking is linked to one property.
- Each booking can be associated with a payment.

### Reviews
Represents feedback left by users about properties.
- `id`: Unique identifier for each review.
- `user_id`: The user who wrote the review.
- `property_id`: The property being reviewed.
- `rating`: Numeric rating (e.g., 1 to 5).
- `comment`: Text feedback provided by the user.

**Relationships:**
- Each review is written by one user.
- Each review is for one property.

### Payments
Represents transactions related to property bookings.
- `id`: Unique identifier for each payment.
- `booking_id`: The booking associated with the payment.
- `amount`: Total amount paid.
- `payment_date`: Date and time of the transaction.
- `status`: Payment status (e.g., successful, failed, pending).

**Relationships:**
- Each payment is linked to one booking.


## Feature Breakdown

### User Management
Allows users to register, authenticate, and manage their profiles securely. This feature supports both guests and hosts, enabling role-based access to platform functionalities such as listing properties or making bookings.

### Property Management
Enables hosts to create, update, retrieve, and delete property listings. This feature ensures that detailed and accurate information about available properties is maintained, including descriptions, locations, and pricing.

### Booking System
Allows users to reserve properties by specifying check-in and check-out dates. It manages booking records, prevents date conflicts, and ensures hosts and guests have access to their booking history.

### Payment Processing
Handles financial transactions associated with bookings. It ensures payments are securely processed, recorded, and linked to their respective bookings, allowing for future tracking and potential refunds.

### Review System
Enables users to provide ratings and feedback on properties they have stayed at. This feature helps build trust within the platform and informs future guests about the quality of listings.

### Data Optimization
Implements database indexing and caching strategies to enhance performance. This ensures fast retrieval of frequently accessed data and reduces the load on the backend infrastructure during high-traffic periods.
