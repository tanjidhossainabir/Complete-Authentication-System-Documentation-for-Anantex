# Complete-Authentication-System-Documentation-for-Anantex
complete authentication system_requirements.
# Anantex Authentication System 🔐

A complete Django authentication system for medical platform with doctor and patient roles.

## 🌟 Features

- **User Registration** with role selection (Doctor/Patient)
- **Secure Login/Logout** system  
- **Custom User Model** with extended fields
- **Django Admin Interface** for user management
- **Responsive Design** with modern UI
- **Country Selection** during registration
- **Password Validation** and security

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Django 4.0+
- Basic knowledge of Django

### Step 1: Project Setup

#### 1.1 Create Project Directory
```
mkdir anantex_project
cd anantex_project

```
1.2 Create Virtual Environment
```
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```
```1.3 Install Dependencies

pip install Django


```
Step 2: Project Structure
Create the following structure:


```anantex_project/
├── manage.py
├── requirements.txt
├── anantex/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── auth_app/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── views.py
│   └── urls.py
├── templates/
│   ├── index.html
│   ├── login.html
│   └── signup.html
└── README.md
```

Step 3: Configuration
3.1 Update settings.py
Add the following to your settings.py:
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'auth_app',
]

AUTH_USER_MODEL = 'auth_app.CustomUser'
LOGIN_URL = 'login'
LOGIN_REDIRECT_URL = 'dashboard'
LOGOUT_REDIRECT_URL = 'home'

```
3.2 Create Custom User Model
In auth_app/models.py:
```
from django.contrib.auth.models import AbstractUser
from django.db import models

class CustomUser(AbstractUser):
    USER_TYPE_CHOICES = (
        ('doctor', 'Doctor'),
        ('patient', 'Patient'),
    )
    
    user_type = models.CharField(max_length=10, choices=USER_TYPE_CHOICES)
    country = models.CharField(max_length=50)

```
Step 4: Database Setup
4.1 Run Migrations
```
python manage.py makemigrations
python manage.py migrate

```
4.2 Create Superuser
```
python manage.py createsuperuser
```

```Step 5: Run Development Server

python manage.py runserver

```
Visit: http://localhost:8000

```📁 Project Structure Details
```
Backend Structure

```anantex_project/
├── anantex/          # Project configuration
├── auth_app/         # Authentication application
├── templates/        # HTML templates
└── manage.py         # Django management script


```
Key Files
models.py - Custom user model with doctor/patient roles

views.py - Authentication logic (login, signup, logout)

urls.py - URL routing configuration

admin.py - Django admin customization


👥 User Types
1. Doctor
Medical professionals

Specialized dashboard access

Patient management capabilities
2. Patient
Healthcare recipients

Medical record access

Appointment scheduling

🔐 Authentication Flow
Registration Process
User visits signup page

Selects role (Doctor/Patient)

Fills personal information

Account created and auto-login

Login Process
User enters credentials

System authenticates

Redirect to role-specific dashboard

Logout Process
User clicks logout

Session terminated

Redirect to home page

🛠️ API Endpoints
Method	Endpoint	Description
GET	/	Home page
GET	/auth/signup/	Registration page
POST	/auth/signup/	Create new account
GET	/auth/login/	Login page
POST	/auth/login/	Authenticate user
GET	/auth/logout/	Logout user
GET	/auth/dashboard/	User dashboard
🎨 Frontend Templates
Home Page (index.html)
Welcome message

Login/Signup buttons

Platform introduction

Login Page (login.html)
Email/Password form

Remember me option

Forgot password link

Signup Page (signup.html)
Personal information form

Role selection (Doctor/Patient)

Country dropdown

Password confirmation

⚙️ Configuration
Database
Default: SQLite (development)

Recommended: PostgreSQL (production)

Security Settings

```# In settings.py
DEBUG = False  # Set to False in production
ALLOWED_HOSTS = ['yourdomain.com', 'localhost']
CSRF_TRUSTED_ORIGINS = ['https://yourdomain.com']

```
Static Files

```
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

```
🚀 Deployment
Production Checklist
Set DEBUG = False

Configure production database

Set up static files serving

Configure ALLOWED_HOSTS

Set secure SECRET_KEY

Enable HTTPS

Set up error logging

Deployment Options
Heroku: Simple PaaS deployment

AWS EC2: Full control VPS

PythonAnywhere: Easy Django hosting

DigitalOcean: Scalable droplets

🐛 Troubleshooting
Common Issues
1. Migration Errors

```
# Solution:
python manage.py makemigrations auth_app
python manage.py migrate

```
2. Static Files Not Loading
```
# In settings.py
STATICFILES_DIRS = [BASE_DIR / "static"]

```
3. Template Not Found
```
# Ensure templates directory is included
TEMPLATES = [
    {
        'DIRS': [BASE_DIR / 'templates'],
    },
]

```
🤝 Contributing
Fork the repository

Create feature branch (git checkout -b feature/AmazingFeature)

Commit changes (git commit -m 'Add AmazingFeature')

Push to branch (git push origin feature/AmazingFeature)

Open Pull Request

📄 License
This project is licensed under the MIT License - see the LICENSE.md file for details.

🙏 Acknowledgments
Django Foundation for the amazing web framework

Medical community for inspiration

Contributors and testers

Live Demo: anantex.org
GitHub Repository: github.com/anantex/auth-system
Documentation: docs.anantex.org

<div align="center">
Built with ❤️ for the Medical Community
</div> ```
📋 Additional Files
requirements.txt

```
Django>=4.0,<5.0

```
.gitignore

```
# Django
*.pyc
__pycache__/
db.sqlite3

# Environment
.env
venv/

# IDE
.vscode/
.idea/

# Static files
staticfiles/
media/
