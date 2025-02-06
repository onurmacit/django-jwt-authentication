Django JWT Authentication
This repository demonstrates how to implement JWT (JSON Web Token) authentication in Django Rest Framework (DRF). It includes user registration, login, and token refresh functionality, along with best practices for securing your API.

Features
User Registration: Create a new user account with a secure password (passwords are hidden in API responses).

User Login: Authenticate users and generate JWT tokens (access and refresh tokens).

Token Refresh: Obtain a new access token using the refresh token.

Password Security: Passwords are hashed and never exposed in API responses or logs.

Custom User Model: Extend Django's default user model with additional fields (e.g., phone number).

Best Practices: Follows security and performance best practices for JWT authentication.

Table of Contents
Installation

Setup

API Endpoints

Usage Examples

Best Practices

Contributing

License

Installation
Prerequisites
Python 3.8 or higher

Django 4.0 or higher

Django Rest Framework (DRF)

djangorestframework-simplejwt

Steps
Clone the repository:

bash
Copy
git clone https://github.com/your-username/django-jwt-authentication.git
cd django-jwt-authentication
Install dependencies:

bash
Copy
pip install -r requirements.txt
Setup
Environment Variables:
Create a .env file in the root directory and add the following:

Copy
SECRET_KEY=your-secret-key
DEBUG=True
Run Migrations:
Apply the database migrations:

bash
Copy
python manage.py migrate
Start the Server:
Run the development server:

bash
Copy
python manage.py runserver
Access the API:
The API will be available at http://127.0.0.1:8000/.

API Endpoints
1. Register a New User
URL: /api/register/

Method: POST

Request Body:

json
Copy
{
  "username": "your_username",
  "email": "your_email@example.com",
  "password": "your_password"
}
Response:

json
Copy
{
  "username": "your_username",
  "email": "your_email@example.com"
}
2. Login
URL: /api/login/

Method: POST

Request Body:

json
Copy
{
  "username": "your_username",
  "password": "your_password"
}
Response:

json
Copy
{
  "access": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "refresh": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
3. Refresh Token
URL: /api/token/refresh/

Method: POST

Request Body:

json
Copy
{
  "refresh": "your_refresh_token"
}
Response:

json
Copy
{
  "access": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
Usage Examples
Register a New User
bash
Copy
curl -X POST http://127.0.0.1:8000/api/register/ \
-H "Content-Type: application/json" \
-d '{
  "username": "testuser",
  "email": "testuser@example.com",
  "password": "testpassword123"
}'
Login
bash
Copy
curl -X POST http://127.0.0.1:8000/api/login/ \
-H "Content-Type: application/json" \
-d '{
  "username": "testuser",
  "password": "testpassword123"
}'
Refresh Token
bash
Copy
curl -X POST http://127.0.0.1:8000/api/token/refresh/ \
-H "Content-Type: application/json" \
-d '{
  "refresh": "your_refresh_token"
}'
Best Practices
Short-Lived Access Tokens: Access tokens expire after 30 minutes to minimize security risks.

Token Rotation: Refresh tokens are rotated after each use to enhance security.

Password Security: Passwords are hashed using Django's built-in password hashing and are never exposed in API responses.

HTTPS: Always use HTTPS in production to encrypt data transmitted between the client and server.

Rate Limiting: Protect login and token endpoints from brute-force attacks by implementing rate limiting.

Contributing
Contributions are welcome! If you'd like to contribute, please follow these steps:

Fork the repository.

Create a new branch for your feature or bugfix.

Commit your changes and push to the branch.

Submit a pull request.

License
This project is licensed under the MIT License. See the LICENSE file for details.

Acknowledgments
Django Rest Framework

djangorestframework-simplejwt

Django Documentation
