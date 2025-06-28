# Backend Requirement Specifications — Airbnb Clone

## 📌 Overview
This document outlines the technical and functional requirements for core backend features of the Airbnb Clone, including API endpoints, input/output details, validation rules, and performance expectations.

---

## 1. 🔐 User Authentication

### Functional Requirements
- Users must be able to register and log in securely.
- Authentication via email/password with optional OAuth (Google, Facebook).
- Passwords must be hashed (e.g., bcrypt).
- Issue and verify JWT tokens for secure sessions.

### API Endpoints
| Method | Endpoint         | Description              |
|--------|------------------|--------------------------|
| POST   | `/api/auth/register` | Register new user     |
| POST   | `/api/auth/login`    | User login            |
| GET    | `/api/auth/profile`  | Get logged-in user    |

### Input/Output
#### `POST /api/auth/register`
**Input JSON**
```json
{
  "email": "user@example.com",
  "password": "securePassword123",
  "role": "guest" // or "host"
}
### ✅ Output

- **201 Created** with property ID  
- **401 Unauthorized** if not authenticated

---

### 🔎 Validation

- **Title**: non-empty string  
- **Price**: must be a positive number  
- **Location**: must be a valid string  
- Only **hosts** can add/edit/delete properties

---

### ⚙️ Performance Criteria

- CRUD operations must complete under **500ms**  
- Property listing queries should complete under **1s** with filters

---

## 3. 📅 Booking System

### 🔧 Functional Requirements

- Guests can **book available properties**  
- Prevent **overlapping/double bookings**  
- Allow **booking cancellation** with status updates  
- Hosts can **view booking details**

---

### 📡 API Endpoints

| Method | Endpoint               | Description                 |
|--------|------------------------|-----------------------------|
| POST   | `/api/bookings`        | Create a new booking        |
| GET    | `/api/bookings/:id`    | View booking details        |
| DELETE | `/api/bookings/:id`    | Cancel a booking            |
| GET    | `/api/bookings`        | List bookings (host/guest)  |

---

### 📥 Input/Output

#### `POST /api/bookings`

##### ✅ Input JSON
```json
{
  "property_id": "abc123",
  "check_in": "2025-07-01",
  "check_out": "2025-07-05"
}

{
  "title": "Cozy Studio Apartment",
  "description": "Perfect for short stays",
  "location": "Addis Ababa, Ethiopia",
  "price": 35,
  "availability": "2025-07-01 to 2025-07-10",
  "amenities": ["WiFi", "Kitchen"]
}
{
  "property_id": "abc123",
  "check_in": "2025-07-01",
  "check_out": "2025-07-05"
}

