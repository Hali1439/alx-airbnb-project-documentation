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
