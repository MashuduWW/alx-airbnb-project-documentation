\# Backend Requirement Specifications

\---

\## 1. User Authentication

\### Overview

Provides secure login/logout, registration, and session management using JWT.

\### API Endpoints

\- \*\*POST /api/auth/register\*\*

\- \*\*POST /api/auth/login\*\*

\- \*\*POST /api/auth/logout\*\*

\- \*\*GET /api/auth/me\*\*

\### Input/Output Specifications

\#### POST /api/auth/register

\*\*Input (JSON)\*\*:

\`\`\`json

{

"first_name": "John",

"last_name": "Doe",

"email": "<john@example.com>",

"password": "SecurePass123"

}

Output (Success - 201):

{

"user_id": "uuid",

"message": "Registration successful"

}

POST /api/auth/login

Input:

{

"email": "<john@example.com>",

"password": "SecurePass123"

}

Output:

{

"token": "JWT-Token-Here",

"expires_in": 3600

}

Validation Rules

Email must be valid and unique

Password: min 8 characters, must include a number and a symbol

Performance Criteria

Token generation time < 500ms

Max login attempts: 5 per IP/hour

2\. Property Management

Overview

Allows hosts to create, update, retrieve, and delete property listings.

API Endpoints

POST /api/properties/

GET /api/properties/{id}

PUT /api/properties/{id}

DELETE /api/properties/{id}

GET /api/properties?location=&type=&price_range=

Input/Output Specifications

POST /api/properties/

Input:

{

"title": "Seaside Apartment",

"description": "A cozy place near the beach",

"price_per_night": 120,

"location": "Cape Town",

"amenities": \["WiFi", "Kitchen", "Parking"\],

"images": \["img1.jpg", "img2.jpg"\]

}

Output:

{

"property_id": "uuid",

"message": "Property created"

}

Validation Rules

title, price_per_night, location are required

Price must be a positive integer

Max 10 images per listing

Performance Criteria

Search filter response < 700ms

Image upload size: ≤ 5MB per image

3\. Booking System

Overview

Enables guests to book available properties with date validation and payment linking.

API Endpoints

POST /api/bookings/

GET /api/bookings/user/{user_id}

DELETE /api/bookings/{booking_id}

Input/Output Specifications

POST /api/bookings/

Input:

{

"property_id": "uuid",

"guest_id": "uuid",

"check_in": "2025-07-15",

"check_out": "2025-07-20"

}

Output:

{

"booking_id": "uuid",

"total_price": 600,

"status": "confirmed"

}

Validation Rules

Dates must not overlap with existing bookings

Check-in must be before check-out

Minimum stay: 1 night

Performance Criteria

Availability check: ≤ 500ms

Supports 100+ concurrent bookings per second
