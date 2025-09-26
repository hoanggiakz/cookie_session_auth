# Project README

## Table of Contents
- [1. Run Server](#1-run-server)
- [2. API Testing with Postman](#2-api-testing-with-postman)
  - [a. Register a new user](#a-register-a-new-user)
  - [b. Login](#b-login)
  - [c. Go to Profile (Protected route)](#c-go-to-profile-protected-route)
  - [d. Logout](#d-logout)
  - [e. Check Cookie Deleted in Database](#e-check-cookie-deleted-in-database)
- [3. Notes](#3-notes)


## 1. Run Server
npm install
node app.js
Server will run on:
👉 http://localhost:3000

## 2. Run Server**
We use Postman to test all APIs.
After each request, a session cookie (connect.sid) will be stored in MongoDB and also sent back to the client.

# a. Register a new user
Endpoint: POST /auth/register

Body (JSON):

json
Copy code
{
  "username": "admin",
  "password": "12345"
}
Expected result: User registered successfully.

# b. Login
Endpoint: POST /auth/login

Body (JSON):

json
Copy code
{
  "username": "admin",
  "password": "12345"
}
Expected result: Login successful and connect.sid cookie set.

# c. Go to Profile (Protected route)
Endpoint: GET /auth/profile

Requirement: Must include session cookie (connect.sid) from login.

Expected result: Return user info (without password).

# d. Logout
Endpoint: GET /auth/logout

Expected result: Session destroyed, cookie cleared.

# e. Check Cookie Deleted in Database
After logout, verify in MongoDB that the session document was deleted from the sessions collection.
