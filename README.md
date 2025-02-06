# Django JWT Authentication

This repository demonstrates how to implement JWT authentication in Django Rest Framework (DRF). It includes:
- User registration and login endpoints.
- Secure token generation and refresh mechanisms.
- **Password hiding** in API responses and admin panel.
- Best practices for JWT authentication.

## Features
- **Register**: Create a new user account (passwords are hidden in responses).
- **Login**: Authenticate and receive JWT tokens.
- **Token Refresh**: Obtain a new access token using the refresh token.

## Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/django-jwt-authentication.git
   cd django-jwt-authentication
