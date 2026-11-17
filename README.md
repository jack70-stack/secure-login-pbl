Secure Login System

1. Project Overview

The Secure Login System is a web application developed using Python and Flask. It provides user registration, login, session management, and logout functionality.

The project focuses on implementing essential web application security mechanisms to protect user accounts and prevent common attacks.

2. Technologies Used

* Python
* Flask
* SQLite
* HTML
* Werkzeug
* Ubuntu on WSL

3. Main Features

* User registration
* User login and authentication
* Password hashing
* SQLite database integration
* Session management
* Protected dashboard
* Secure logout using POST requests
* CSRF token validation
* Username and password length validation

4. Security Implementations

Password Hashing

Passwords are hashed using Werkzeug’s generate_password_hash() before being stored in the database.

SQL Injection Protection

Parameterized SQL queries are used for login and registration database operations.

CSRF Protection

CSRF tokens are generated using Python’s secrets module. POST requests are checked for valid tokens.

Session Security

The application uses Flask sessions and configures:

* HttpOnly session cookies
* SameSite=Lax cookie policy

Authentication Protection

Unauthenticated users cannot access the protected dashboard.

Input Validation

Usernames must contain between 3 and 30 characters. Passwords must contain at least 8 characters.

5. Database

The project uses SQLite with a database named database.db.

The users table contains:

* id
* username
* password_hash

Passwords are stored as hashes rather than plaintext.

6. Project Structure

secure-login-pbl/
├── app.py
├── database.db
├── requirements.txt
├── README.md
├── templates/
│   ├── dashboard.html
│   ├── login.html
│   └── register.html
└── static/

7. Installation and Execution

Clone or download the project and open its directory.

Create and activate a virtual environment:

python3 -m venv .venv
source .venv/bin/activate

Install dependencies:

pip install -r requirements.txt

For a deployment configuration, set a strong secret key through an environment variable:

export SECRET_KEY="$(python -c 'import secrets; print(secrets.token_hex(32))')"

Start the application:

python app.py

Open the application in a browser:

http://127.0.0.1:5000

8. Security Testing

The following checks were performed:

* Successful user registration and login.
* Successful logout.
* Protection of the dashboard against unauthenticated access.
* Missing CSRF token rejected.
* Invalid CSRF token rejected.
* SQL injection test input rejected during login.
* Password hashes verified in the SQLite database.
* Parameterized SQL confirmed in login and registration queries.

9. Limitations and Future Improvements

Possible future improvements include:

* Stronger password policy and common-password blocking.
* Login rate limiting.
* Password reset functionality.
* Multi-factor authentication.
* Improved deployment configuration.
* HTTPS deployment.

10. Conclusion

This project demonstrates the development of a basic secure authentication system using Python, Flask, and SQLite. It applies important security practices such as password hashing, parameterized SQL queries, CSRF protection, session management, and authentication controls.


