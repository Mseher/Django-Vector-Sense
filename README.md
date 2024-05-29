
## Django Vector Sense App Documentation

### Table of Contents

1. [Project Overview](#project-overview)
2. [Requirements](#requirements)
3. [Installation](#installation)
4. [Configuration](#configuration)
5. [Running the Project](#running-the-project)
6. [Project Structure](#project-structure)
7. [Features](#features)
8. [Usage](#usage)
9. [License](#license)

---

### 1. Project Overview

The Django Vector Sense App is a geocoder application designed to monitor and manage data related to vector-borne diseases. The application integrates several technologies to provide a comprehensive toolset for disease monitoring, hotspot identification, and outbreak prevention. The app includes functionalities for user management, data visualization, and integration with external services such as Google Maps.

### 2. Requirements

#### Software Requirements

- Python 3.8+
- Django 4.2.5
- PostgreSQL or MySQL
- Virtual Environment

#### Python Packages

List of required Python packages included in `requirements.txt`:

```plaintext
asgiref==3.7.2
certifi==2023.7.22
chardet==5.2.0
charset-normalizer==3.2.0
Django==4.2.5
django-cors-headers==4.2.0
django-session-timeout==0.1.0
django-storages==1.14.2
geographiclib==2.0
geopy==2.4.0
googlemaps==4.10.0
idna==3.4
Pillow==10.3.0
psycopg2==2.9.7
pytz==2023.3.post1
requests==2.31.0
six==1.16.0
sqlparse==0.4.4
typing_extensions==4.8.0
urllib3==2.0.5
```

### 3. Installation

#### Step 1: Clone the Repository

```bash
git clone https://github.com/your_username/django_vector_sense.git
cd django_vector_sense
```

#### Step 2: Create and Activate a Virtual Environment

```bash
python3 -m venv myenv
source myenv/bin/activate  # On Windows: myenv\Scripts\activate
```

#### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

#### Step 4: Install Packages from https://test.pypi.org/project/vector-sense-blog-users-mysql/1.0/

```bash
pip install -i https://test.pypi.org/simple/ vector-sense-blog-users-mysql==1.0
```

### 4. Configuration

#### Step 1: Database Configuration

Update `settings.py` with your database configuration. For PostgreSQL:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'your_database_name',
        'USER': 'your_database_user',
        'PASSWORD': 'your_database_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

#### Step 2: AWS S3 Configuration

Add AWS S3 settings to `settings.py` for media storage:

```python
AWS_ACCESS_KEY_ID = os.environ.get('AWS_ACCESS_KEY_ID')
AWS_SECRET_ACCESS_KEY = os.environ.get('AWS_SECRET_ACCESS_KEY')
AWS_STORAGE_BUCKET_NAME = os.environ.get('AWS_STORAGE_BUCKET_NAME')
AWS_S3_REGION_NAME = os.environ.get('AWS_S3_REGION_NAME', 'us-east-1')
AWS_S3_CUSTOM_DOMAIN = f'{AWS_STORAGE_BUCKET_NAME}.s3.amazonaws.com'

DEFAULT_FILE_STORAGE = 'storages.backends.s3boto3.S3Boto3Storage'
MEDIA_URL = f'https://{AWS_S3_CUSTOM_DOMAIN}/media/'
```

### 5. Running the Project

#### Step 1: Apply Migrations

```bash
python manage.py migrate
```

#### Step 2: Create a Superuser

```bash
python manage.py createsuperuser
```

#### Step 3: Run the Development Server

```bash
python manage.py runserver
```

Access the application at `http://localhost:8000`.

### 6. Project Structure

```plaintext
django_vector_sense/
├── manage.py
├── myenv/
├── django_proj/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
├── media/
│   └── profile_pics/
│       ├── default.jpg
│       └── ...
├── static/
│   ├── css/
│   ├── js/
│   └── ...
├── requirements.txt
├── README.rst
```

### 7. Features

- **User Management**: User registration, login, profile management.
- **Geocoding**: Integration with Google Maps for geocoding.
- **Data Storage**: Media files stored in AWS S3.
- **Data Visualization**: Display and analyze vector-borne disease data.
- **Security**: Session management, CSRF protection.

### 8. Usage

#### Adding a New User

1. Navigate to the registration page.
2. Fill out the registration form and submit.
3. Verify the email address (if email verification is implemented).
4. Log in with the new credentials.

#### Managing User Profiles

1. Log in to the application.
2. Navigate to the profile page.
3. Upload a profile picture and update personal information.
4. Save changes.

#### Viewing and Managing Data

1. Log in as an admin user.
2. Navigate to the admin panel.
3. Manage users, view geocoding data, and perform administrative tasks.

### 9. License

This project is licensed under the MIT License. See the `LICENSE` file for more information.

---
