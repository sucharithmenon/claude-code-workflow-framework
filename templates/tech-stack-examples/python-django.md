# Python + Django CCWF Customization

## Customize Your .claude/commands/issue.md

Replace the testing section with:

```markdown
# TEST
- Use puppeteer via MCP to test the changes if you have made changes to the UI
- Write pytest tests to describe the expected behavior of your code
- Write Django test cases for models, views, and forms
- Run the full test suite: `python manage.py test` or `pytest`
- Run coverage analysis: `coverage run --source='.' manage.py test && coverage report`
- Run Django system checks: `python manage.py check`
- Run migrations check: `python manage.py makemigrations --check --dry-run`
- If the tests are failing, fix them
- Ensure that all tests are passing before moving on to the next step
```

## Add to Your CLAUDE.md

```markdown
# Development Commands

## Django Development
```bash
# Virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Dependencies
pip install -r requirements.txt
pip install -r requirements-dev.txt

# Development server
python manage.py runserver      # Start development server (http://127.0.0.1:8000)
python manage.py shell          # Django shell
python manage.py dbshell        # Database shell

# Database
python manage.py makemigrations # Create migrations
python manage.py migrate        # Apply migrations
python manage.py createsuperuser # Create admin user

# Testing
python manage.py test           # Run Django tests
pytest                          # Run pytest tests
coverage run --source='.' manage.py test && coverage report

# Static files
python manage.py collectstatic  # Collect static files
python manage.py runserver --insecure  # Serve static files in development

# Quality checks
python manage.py check          # System checks
python manage.py check --deploy # Deployment checks
black .                         # Code formatting
flake8                          # Linting
mypy .                          # Type checking
```

## Project Structure
```
project_name/
├── project_name/               # Project configuration
│   ├── __init__.py
│   ├── settings/               # Split settings
│   │   ├── __init__.py
│   │   ├── base.py
│   │   ├── development.py
│   │   └── production.py
│   ├── urls.py
│   └── wsgi.py
├── apps/                       # Django apps
│   ├── users/
│   ├── core/
│   └── api/
├── static/                     # Static files
├── media/                      # User uploads
├── templates/                  # HTML templates
├── tests/                      # Test files
├── requirements/               # Requirements files
│   ├── base.txt
│   ├── development.txt
│   └── production.txt
└── manage.py
```
```

## Example Infrastructure Issues for Django

### 1. Set up Testing Framework
```markdown
## Summary
Configure pytest, Django test framework, and coverage reporting

## Acceptance Criteria
- [ ] pytest-django installed and configured
- [ ] Django test settings configured
- [ ] Factory Boy set up for test data generation
- [ ] Coverage reporting configured
- [ ] Test database configuration
- [ ] Example test files created for models, views, and forms

## Technical Notes
- Configure pytest.ini with Django settings
- Use separate test database
- Set up fixtures and factories for consistent test data
- Configure coverage to exclude migrations and settings
```

### 2. Set up Development Environment
```markdown
## Summary
Configure Django settings for development with debug tools and environment variables

## Acceptance Criteria
- [ ] Settings split into base/development/production
- [ ] Environment variables configured with python-decouple
- [ ] Django Debug Toolbar installed and configured
- [ ] Logging configuration set up
- [ ] Development database configured
- [ ] Static files handling configured

## Technical Notes
- Use django-environ for environment variables
- Configure different databases for dev/test/prod
- Set up proper logging levels and handlers
```

### 3. Set up Database and Models
```markdown
## Summary
Configure database, create initial models, and set up migrations

## Acceptance Criteria
- [ ] Database connection configured
- [ ] Initial models created with proper relationships
- [ ] Migrations created and applied
- [ ] Database indexes configured for performance
- [ ] Model validation and constraints set up
- [ ] Admin interface configured for models

## Technical Notes
- Use PostgreSQL for production-like development
- Add proper __str__ methods and Meta classes
- Configure database connection pooling if needed
```

## Common Django Patterns

### Model Example
```python
# apps/users/models.py
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    email = models.EmailField(unique=True)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    
    USERNAME_FIELD = 'email'
    REQUIRED_FIELDS = ['username']

class Profile(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE)
    bio = models.TextField(blank=True)
    avatar = models.ImageField(upload_to='avatars/', blank=True)
    
    def __str__(self):
        return f"{self.user.username}'s Profile"
```

### View Example
```python
# apps/users/views.py
from django.contrib.auth.mixins import LoginRequiredMixin
from django.views.generic import DetailView, UpdateView
from .models import Profile

class ProfileDetailView(LoginRequiredMixin, DetailView):
    model = Profile
    template_name = 'users/profile_detail.html'
    context_object_name = 'profile'

class ProfileUpdateView(LoginRequiredMixin, UpdateView):
    model = Profile
    fields = ['bio', 'avatar']
    template_name = 'users/profile_update.html'
    
    def get_object(self):
        return self.request.user.profile
```

### Test Example
```python
# tests/test_users.py
import pytest
from django.test import TestCase
from django.contrib.auth import get_user_model
from apps.users.models import Profile

User = get_user_model()

class TestUserModel(TestCase):
    def setUp(self):
        self.user = User.objects.create_user(
            username='testuser',
            email='test@example.com',
            password='testpass123'
        )
    
    def test_user_creation(self):
        self.assertEqual(self.user.email, 'test@example.com')
        self.assertTrue(self.user.check_password('testpass123'))
    
    def test_profile_creation(self):
        profile = Profile.objects.create(
            user=self.user,
            bio='Test bio'
        )
        self.assertEqual(str(profile), "testuser's Profile")

@pytest.mark.django_db
def test_user_registration():
    user = User.objects.create_user(
        username='pytest_user',
        email='pytest@example.com',
        password='testpass123'
    )
    assert user.email == 'pytest@example.com'
    assert user.is_active
```

## Recommended Dependencies

```txt
# requirements/base.txt
Django>=5.0.0
psycopg2-binary>=2.9.0
Pillow>=10.0.0
django-environ>=0.11.0

# requirements/development.txt
-r base.txt
django-debug-toolbar>=4.2.0
pytest-django>=4.5.0
factory-boy>=3.3.0
coverage>=7.3.0
black>=23.0.0
flake8>=6.0.0
mypy>=1.5.0

# requirements/production.txt
-r base.txt
gunicorn>=21.2.0
whitenoise>=6.5.0
```

## Django Best Practices for CCWF

1. **Split Settings**: Use separate settings files for different environments
2. **Environment Variables**: Store secrets and configuration in environment variables
3. **Database Migrations**: Always create and review migrations before applying
4. **Testing**: Write tests for models, views, forms, and business logic
5. **Security**: Use Django's built-in security features and keep dependencies updated
6. **Performance**: Use select_related/prefetch_related, database indexes, and caching
7. **Code Quality**: Use Black, flake8, and mypy for consistent code style