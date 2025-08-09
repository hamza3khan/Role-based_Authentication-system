 Role-Based Authentication and Authorization System (FastAPI)

Project Description

This project is a secure backend authentication system built with FastAPI.  
It implements role-based access control (RBAC), allowing users to register, log in, and access different routes depending on their assigned roles (e.g., `user`, `admin`).

The project ensures:
- Secure password hashing using bcrypt.
- Authentication via JWT (JSON Web Tokens)
- Role-based authorization for protected endpoints.


Technologies Used
   FastAPI — Web framework
   Uvicorn — ASGI server
   SQLAlchemy — ORM for database
   Passlib (bcrypt) — Secure password hashing
   Python-Jose— JWT handling
   SQLite— Lightweight database (can be replaced with MySQL/PostgreSQL)

---

 Project Structure
 role_based_auth/
│
├── main.py # Entry point for FastAPI app
├── database.py # Database connection setup
├── models.py # SQLAlchemy models
├── schemas.py # Pydantic schemas
├── auth.py # Authentication logic (JWT, password hashing)
├── crud.py # Database queries (Create, Read, Update, Delete)
└── README.md # Project documentation

 Install Dependencies
<pip install fastapi uvicorn sqlalchemy passlib[bcrypt] python-jose>

Run the Application
 uvicorn app.main:app --reload  


 http://127.0.0.1:8000


 API Endpoints
 Public Routes
Method | 	Endpoint  |    |   Description
POST	 | /register	|    |   Register a new user
POST	 |  /token	  |    |   Login and get JWT token

 
 Protected Routes (Authentication Required)
Method	Endpoint	Role	   Description
GET	   /profile  	User	   View your profile
GET	  /admin	  Admin	     Access admin panel


How It Works
User Registration
User sends username and password to /register.
Password is hashed using bcrypt and stored in the database.

Login & JWT Token
User sends username and password to /token.
If valid, a JWT token is generated and returned.

Authorization
Users send their JWT token in the Authorization header:

makefile

Authorization: Bearer <your_token>
The system checks:

Token validity.
User role for accessing certain endpoints.
Role-Based Access Control

Example:
/profile → Any authenticated user.
/admin → Only users with role="admin".



Testing the API
Once running, visit:

Swagger Docs: http://127.0.0.1:8000/docs


Security Features
.Password hashing with bcrypt (Passlib)
.JWT token authentication
.Role-based authorization checks
.No plain-text password storage



Conclusion

This project demonstrates:
How to use FastAPI for secure authentication.
How to implement role-based authorization.
How to manage sessions using JWT tokens.

 
