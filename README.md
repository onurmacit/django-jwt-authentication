# Django JWT Authentication

This repository demonstrates how to implement **JWT (JSON Web Token) authentication** in Django Rest Framework (DRF). It includes user registration, login, and token refresh functionality, along with best practices for securing your API. You can access the [Article](https://medium.com/@onurmaciit/mastering-jwt-authentication-in-django-rest-framework-best-practices-and-techniques-d47f906f530a)
 about this repo here 


## Features
- **User Registration**: Create a new user account with a secure password (passwords are hidden in API responses).
- **User Login**: Authenticate users and generate JWT tokens (access and refresh tokens).
- **Token Refresh**: Obtain a new access token using the refresh token.
- **Password Security**: Passwords are hashed and never exposed in API responses or logs.
- **Custom User Model**: Extend Django's default user model with additional fields (e.g., phone number).
- **Best Practices**: Follows security and performance best practices for JWT authentication.

---

## Table of Contents
1. [Installation](#installation)
2. [Setup](#setup)
3. [API Endpoints](#api-endpoints)
4. [Usage Examples](#usage-examples)
5. [Best Practices](#best-practices)
6. [Contributing](#contributing)
7. [License](#license)

---

## Installation

### Prerequisites
- Python 3.8 or higher
- Django 4.0 or higher
- Django Rest Framework (DRF)
- djangorestframework-simplejwt

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/django-jwt-authentication.git
   cd django-jwt-authentication
2. Install dependencies:

```bash
pip install -r requirements.txt
```

## Setup

1. Environment Variables:
Create a .env file in the root directory and add the following:


```bash
SECRET_KEY=your-secret-key
DEBUG=True
```

2. Run Migrations:
Apply the database migrations:
```bash
python manage.py migrate
```

3. Start the Server:
Run the development server:
```bash
python manage.py runserver
```
4. Access the API:
The API will be available at http://127.0.0.1:8000/.

---

## API Endpoints
### 1. Register a New User
- URL: /api/register/

- Method: POST

- Request Body:
```bash
{
  "username": "your_username",
  "email": "your_email@example.com",
  "password": "your_password"
}
```
- Response:
```bash
{
  "username": "your_username",
  "email": "your_email@example.com"
}
```
### 2. Login
- URL: /api/login/

- Method: POST

- Request Body:
```bash
{
  "username": "your_username",
  "password": "your_password"
}
```
- Response:
```bash
{
  "access": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "refresh": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```
### 3. Refresh Token
- URL: /api/token/refresh/

- Method: POST

- Request Body:
```bash
{
  "refresh": "your_refresh_token"
}
```
- Response:
```bash
{
  "access": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```
---
## Usage Examples

### Register a New User
```bash
curl -X POST http://127.0.0.1:8000/api/register/ \
-H "Content-Type: application/json" \
-d '{
  "username": "testuser",
  "email": "testuser@example.com",
  "password": "testpassword123"
}'
```
### Login
```bash
curl -X POST http://127.0.0.1:8000/api/login/ \
-H "Content-Type: application/json" \
-d '{
  "username": "testuser",
  "password": "testpassword123"
}'
```
### Refresh Token
```bash
curl -X POST http://127.0.0.1:8000/api/token/refresh/ \
-H "Content-Type: application/json" \
-d '{
  "refresh": "your_refresh_token"
}'
```
---

## Best Practices
1. **Short-Lived Access Tokens:** Access tokens expire after 30 minutes to minimize security risks.

2. **Token Rotation:** Refresh tokens are rotated after each use to enhance security.

3. **Password Security:** Passwords are hashed using Django's built-in password hashing and are never exposed in API responses.

4. **HTTPS:** Always use HTTPS in production to encrypt data transmitted between the client and server.

5. **Rate Limiting:** Protect login and token endpoints from brute-force attacks by implementing rate limiting.

---

## Contributing

Contributions are welcome! If you'd like to contribute, please follow these steps:

1. Fork the repository.

2. Create a new branch for your feature or bugfix.

3. Commit your changes and push to the branch.

4. Submit a pull request.

---

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

## Acknowledgments

- [Django Rest Framework](https://www.django-rest-framework.org/)

- [djangorestframework-simplejwt](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/)

- [Django Documentation](https://docs.djangoproject.com/en/5.1/)


