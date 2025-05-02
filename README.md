# airbnb-clone-project
This Project is an Airbnb Clone. It's aimed at simulating a real-world application, An aid in understanding complex architectures, workflows and collaborations, while building and scaling web application. It involves a deep dive into software development, focusing on backend systems, database design, API development, and application security.


## Team Roles
### Backend Developer 
  Designs the server-side logic, build APIs, handles database management, ensures authentication/security, and manages data flow between the server and the frontend.
### Database Administrator (DBA)
  Designs and optimizes the database schema, ensures data integrity, backups, security, and query performance tuning.
### DevOps Engineer
  Manages server deployment, CI/CD pipelines, cloud infrastructure (AWS, Azure, GCP, Linode), monitoring, scaling, backups, and ensures uptime and reliability.
### Security Engineer
  Focussing on protecting user data, securing APIs, ensuring safe authentication/authorization flows (OAuth, JWT), and defending against common vulnerabilities (like SQL injection, XSS, CSRF)
### QA Engineer(Tester)
  Tests the application for bugs, functionality, security vulnerabilities, performance issues, and ensures that the app meets the requirements through manual automated testing.


## Technology Stack
### Django 
  A high-level Python web framework used to build the backend, handle business logic, manage users, properties, bookings, and integrate security features.
### Django REST Framework (DRF)
  An extension of Django for building powerful and flexible RESTful APIs that allow the frontend or other clients to communicate with the backend easily.
### PostgreSQL
  A robust, scalable relational database used to store structured data like user profiles, property listings, bookings, reviews, and transactions.
### GraphQL 
  An alternative to traditional REST APIs, enabling clients to request exactly the data they need, improving API performance and flexibility.
### Celery 
  A task queue system used for handling asynchronous tasks like sending emails, notifications or processing background jobs( e.g., confirming a booking).
### Redis
  An in-memory data store used as a messages broker for Celery and also for caching to speed up API responses and session management.
### Docker 
  Containerize the entire application (backend, database, task queues) to ensure consistent development, testing, and production environments.
### CI/CD Pipelines
   Automates testing, building, and deploying the project ensuring faster, safer updates and maintaining code quality through continuous integration and delivery practices.


## Database Design
### Entities and Fields
#### 1. Users 
. id: Unique identifier
. name: Full name
. email: User's email address
. password_hash: Hashed password for authentication
. is_host: Boolean indicating if the user can list properties

#### 2. Properties
. id: Unique identifier
. owner_id: Foreign key referencing Users
. title: Property title 
. description: Detailed description
. location: Address or geographic location

#### 3. Booking 
. id: unique identifier 
. property_id: Foreign key referencing Properties 
. user_id: Foreign key referencing Users
. start_date: Date booking starts
. end_date: Date booking ends

#### 4. Reviews
. id: Unique identifier
. property_id: Foreign key referencing Properties
. user_id: Foreign key referencing Users
. rating: Numerical ratin ( e.g., 1 - 10 )
. comment: Optional text feedback

#### 5. Payments
. id: Unique identifier
. user_id: Foreign key referencing Users
. booking_id: Foreign key referencing Bookings
. amount: Payment amount
. payment_status: Status (e.g. pending, completed, failed)

### Entity Relationships
#### . User <-> Properties:
. A user (host) can own multiple properties.
#### . User <-> Bookings:
. A user (guest) can make multiple bookings. 
#### . property <-> Bookings:
. A property can have multiple bookings over time.
#### . User <-> Reviews:
. A user can write multiple reviews for different properties.
#### . Property <-> Reviews:
. A property can have multiple reviews from different users. 
#### . Booking <-> Payment:
. Each booking should have one associated payment.


## Feature Breakdown 
### User Management
Handles user registration, login, authentication, and profile management. It ensures users can securely access and manage their accounts, whether they are guests or hosts.
### Property Management
Allows hosts to create, update, and delete property listings with detailed descriptions, pricing, and phostes. This feature forms the core of the platform by enabling the listing of rentable spaces.
### Booking System
Enables guests to search for properties, make bookings, and manage reservationis. It handles availability checks, booking confirmations, and ensures a smooth reservation process.
### Review and Rating System
Lets users leave reviews and ratings for properties they have stayed at. This promotes transparency, trust, and helps future guests make informed decisions.
### Payment Integration
Facilitates secure payment processing for bookings through trusted third-party services (e.g., Stripe or PayPal). It ensures that transactions are seamless and that hosts receive payments efficiently.
### Search and Filter Functionality 
Provides users with powerful search and filtering tools (e.g., by location, price, amenities). It enhances user experience by helping guests quickly find properties that match their preferences.
### Notifications System
Sends notifications for booking confirmations, payment status updates, and important platform messages. This keeps users informed and engaged throughout their journey.


## API Security
To protect the platform, several key security measures are implemented
### . Authentication: 
  Users authenticate securely using JWT (JSON Web Tokens) to protect access to private endpoints.
### . Authorization: 
  Role-based access control (RBAC) ensures that users can only access or modify resources they own, separating guest, host, and admin privileges. 
### . Rate Limiting: 
  API requests are limited per IP to prevent abuse, brute-force attacks, and ensure fair use of system resources. 
### . Data Validation and Sanitization:
  All incoming data is validated and sanitized to prevent SQL Injection, Cross-Site Scripting (XSS), and other common vulnerabilities. 
### . HTTPS Enforcement: 
  All communications are encrypted over HTTPS to secure sensitive data in transit.
### . Secure Payment Handling: 
  Payments are processed via trusted third-party services (e.g., Stripe), ensuring financial transactios are safe without directly storing sensitive payment data.

## CI/CD Pipeline
CI/CD (Continuous Integration and Continuous Deployment) is the practice of automatically testing, building, and deploying code changes. It ensures that new updates are safely integrated into the project without breaking existing functionality. 
### Why it's Importants:
  . Catches bugs early through automated testing. 
  . Speeds up development and deployment processes. 
  . Reduces manual errors and ensures consistent delivery. 
  . Improves the reliability and quality of the application.
### Tools used:
  . GitHub Actions: For automating testing, building, and deployment workflows.
  . Docker: For containerizing the application to ensure consistent environments.
  . Docker Hub: For storing and managing Docker images.
  . Cloud Platforms (e.g., AWS, Linode, DigitalOcean): For hosting and running the application.
