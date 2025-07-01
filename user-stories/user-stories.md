# User Stories from Use Case Diagram

## 1. User Registration

**As a** new user  
**I want to** create an account with my email and password  
**So that** I can log in and access the platform's features  

### Acceptance Criteria:
- Email and password fields are required
- Email must be unique
- On success, user receives a confirmation message

---

## 2. User Authentication

**As a** registered user  
**I want to** log into the platform securely  
**So that** I can access my personalized dashboard  

### Acceptance Criteria:
- User must enter valid credentials
- JWT token is returned upon success
- Invalid attempts are rejected with an error

---

## 3. Property Management

**As a** host  
**I want to** list and manage my properties  
**So that** potential guests can view and book them  

### Acceptance Criteria:
- Hosts can add, update, and delete properties
- Each listing must include title, description, and pricing
- Images and amenities can be uploaded per property

---

## 4. Property Booking

**As a** guest  
**I want to** search and book available properties  
**So that** I can reserve accommodation for my travel  

### Acceptance Criteria:
- Guests can select check-in/check-out dates
- Bookings are validated against availability
- Guests receive confirmation upon success

---

## 5. Payments

**As a** guest  
**I want to** pay for my bookings securely  
**So that** I can complete my reservation  

### Acceptance Criteria:
- Secure payment gateway is used (e.g., Stripe)
- Payment status is updated in the system
- Hosts receive payout after booking completion
