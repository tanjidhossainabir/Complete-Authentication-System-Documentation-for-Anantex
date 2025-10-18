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

```
anantex_project/
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
