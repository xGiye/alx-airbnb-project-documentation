# Backend Feature Specifications

This document outlines the technical and functional requirements for the key backend features of the **Airbnb Clone** project.

---

## 1. User Authentication

### 🔹 Functional Requirements

- Support for user registration, login, logout, password reset, and profile updates.
- Roles: Guest, Host, Admin.
- Secure authentication using JWT tokens.

### 🔹 API Endpoints

| Method | Endpoint                   | Description                    |
| ------ | -------------------------- | ------------------------------ |
| POST   | /api/users/register/       | Register a new user            |
| POST   | /api/users/login/          | Log in and get JWT token       |
| POST   | /api/users/logout/         | Invalidate the session/token   |
| POST   | /api/users/reset-password/ | Send password reset link/token |
| GET    | /api/users/{id}/           | Fetch user profile             |
| PUT    | /api/users/{id}/           | Update user profile            |

### 🔹 Input/Output Example

**Register Request:**

```json
{
  "username": "johndoe",
  "email": "johndoe@example.com",
  "password": "securePass123"
}
```

## 2. Property Management

### 🔹 Functional Requirements

- Hosts can add, update, or delete property listings.
- Guests can search, view, and filter properties.
- Admins can moderate listings.

### 🔹 API Endpoints

| Method | Endpoint              | Description                        |
| ------ | --------------------- | ---------------------------------- |
| POST   | /api/properties/      | Add new property (HOST)            |
| GET    | /api/properties/      | Let all properties (Public)        |
| GET    | /api/properties/{id}/ | Get details of a selected property |
| PUT    | /api/properties/{id}/ | Update Property (HOST)             |
| DELETE | /api/properties/{id}/ | Delete Property (Host/ Admin)      |

### 🔹 Input/Output Example

**Add Property Request:**

```json
{
  "title": "Luxury 2 Bedroom Apartment",
  "description": "Ocean-view with WiFi and kitchen",
  "location": "Lagos, Nigeria",
  "price_per_night": 150,
  "amenities": ["WiFi", "Air Conditioning", "Pool"]
}
```

**Add Property Response**

```json
{
  "message": "Property created successfully",
  "property_id": 2002
}
```

## 3. Booking System

### 🔹 Functional Requirements

- Guests can make, update, or cancel bookings.
- Hosts can view bookings for their properties.
- Double-booking prevention via date validation.

### 🔹 API Endpoints

| Method | Endpoint              | Description                |
| ------ | --------------------- | -------------------------- |
| POST   | `/api/bookings/`      | Make a new booking         |
| GET    | `/api/bookings/{id}/` | Get booking details        |
| PUT    | `/api/bookings/{id}/` | Update an existing booking |
| DELETE | `/api/bookings/{id}/` | Cancel a booking           |

### 🔹 Input/Output Example

**Make Booking Request:**

```json
{
  "user_id": 1001,
  "property_id": 2002,
  "check_in": "2025-07-15",
  "check_out": "2025-07-20"
}
```

## 4. Payment System

### 🔹 Functional Requirements

- Process payments via integrated payment gateway (e.g., Stripe).
- Admins can monitor payment status and handle disputes.
- Refunds processed to original payment method.

### 🔹 API Endpoints

| Method | Endpoint                | Description                |
| ------ | ----------------------- | -------------------------- |
| POST   | `/api/payments/`        | Process a new payment      |
| GET    | `/api/payments/{id}/`   | Get payment status/details |
| POST   | `/api/payments/refund/` | Issue refund for a booking |

### 🔹 Input/Output Example

**Process Payment Request:**

```json
{
  "booking_id": 3005,
  "amount": 750,
  "payment_method": "card",
  "card_token": "tok_visa"
}
```

**Process Payment Response:**

```json
{
  "message": "Payment completed",
  "payment_id": 4001
}
```

## 5. Review and Rating System

### 🔹 Functional Requirements

- Guests can rate and review properties.
- Hosts can respond to reviews.
- Admins can moderate/delete inappropriate reviews.

### 🔹 API Endpoints

| Method | Endpoint                      | Description                    |
| ------ | ----------------------------- | ------------------------------ |
| POST   | `/api/reviews/`               | Create a review                |
| GET    | `/api/reviews/{property_id}/` | Get all reviews for a property |
| PUT    | `/api/reviews/{id}/`          | Update a review (Guest)        |
| DELETE | `/api/reviews/{id}/`          | Delete review (Guest/Admin)    |
| POST   | `/api/reviews/{id}/response/` | Host responds to a review      |

### 🔹 Input/Output Example

**Submit Review Request:**

```json
{
  "property_id": 2002,
  "user_id": 1001,
  "rating": 4,
  "comment": "Very clean and well-located apartment."
}
```

**Review Response:**

```json
{
  "message": "Review submitted",
  "review_id": 5003
}
```
