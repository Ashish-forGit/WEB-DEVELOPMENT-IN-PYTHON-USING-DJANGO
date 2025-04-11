# Web Development in Python Using Django

## Setting Up Django

To get started with Django for web development, follow these steps:

### 1. Create a Virtual Environment

Set up a virtual environment to isolate project dependencies:
```bash
python -m venv myenv
```

Activate the virtual environment:
- **On Windows:**
  ```bash
  myenv\Scripts\activate.bat
  ```
- **On macOS/Linux:**
  ```bash
  source myenv/bin/activate
  ```

Install Django in your virtual environment:
```bash
pip install django
```

### 2. Create a Django Project

Navigate to your virtual environment:
```bash
cd myenv
```

Start a new Django project:
```bash
django-admin startproject myproject
```

### 3. Run the Development Server

To test the setup, navigate to the project directory and start the development server:
```bash
cd myproject
python manage.py runserver
```

Open your browser and visit [http://127.0.0.1:8000/](http://127.0.0.1:8000/) to see the default Django welcome page.

### 4. Create a New Application

To add functionality to your project, start a new application:
```bash
python manage.py startapp myapp
```
This will create a new directory called `myapp` with the basic structure for a Django application.


---


python manage.py makemigrations
Migrations for 'myapp':
  myapp\migrations\0001_initial.py
    + Create model Emp
python manage.py migrate       
python manage.py shell

>>> from myapp.models import Emp
>>> Emp.objects.all()
<QuerySet []>
>>> Emp.objects.create(first_name="Arpit, last_name="Bala", salary=6000000)

>>> Emp.objects.create(first_name="Arpit", last_name="Bala", salary=6000000) 
<Emp: Emp object (1)>
>>> Emp.objects.all()                                                        
<QuerySet [<Emp: Emp object (1)>]>
>>> Emp.objects.create(first_name="Ashish", last_name="Kr", salary=6000000)   
<Emp: Emp object (2)>
>>> Emp.objects.create(first_name="Sonu", last_name="Kr", salary=6000000)   
<Emp: Emp object (3)>
>>> clear()
Traceback (most recent call last):
  File "<console>", line 1, in <module>
NameError: name 'clear' is not defined
>>> exit() 
now exiting InteractiveConsole...
PS C:\Users\ashis\OneDrive\Desktop\WEB-DEVELOPMENT-IN-PYTHON-USING-DJANGO\myenv\myproject> python manage.py shell         
Python 3.13.1 (tags/v3.13.1:0671451, Dec  3 2024, 19:06:28) [MSC v.1942 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from myapp.models import Emp
>>> e=Emp.objects.get(pk=3)
>>> e.salary =2200000000
>>> e.save()
>>> e=Emp.objects.get(pk=1) 
>>> e.delete()
(1, {'myapp.Emp': 1})


>>python manage.py createsuperuser   
Super user credentials
username =  ashish
password = Ashish@9.9.2001


# Register your models here.
from .models import Emp
admin.site.register(Emp)


python manage.py shell -----------first
Adding user using shell command
from django.contrib.auth.models import user
User.objects.create_user(username="Sujoy",email="sujoy@gmail.com",password='123')

changing username status to staff
 user=User.objects.get(username="Sujoy")
 user.is_staff=True
 user.save()

giving permission using shell commands
 from django.contrib.auth.models import Permission
 from django.contrib.contenttypes.models import ContentType
 from myapp.models import Blogpost
 user=User.objects.get(username="Sujoy")
 content_type=ContentType.objects.get_for_model(Blogpost)
 view_permission=Permission.objects.get(codename='view_blogpost',content_type=content_type,)
 user.user_permissions.add(view_permission)

# Assign multiple permissions to the user
 permissions = Permission.objects.filter(content_type=content_type, codename__in=['view_blogpost', 'change_blogpost', 'delete_blogpost'])

# Assign multiple permissions to the user
user.user_permissions.add(*permissions)

# Give permissions to Groups
from django.contrib.auth.models import Permission,Group
 from django.contrib.contenttypes.models import ContentType
 from myapp.models import Blogpost,Author,Book,Emp
 group=Group.objects.get(username="newgroup")
 content_type1=ContentType.objects.get_for_model(Blogpost)
 content_type2=ContentType.objects.get_for_model(Author)
 content_type3=ContentType.objects.get_for_model(Book)
 content_type4=ContentType.objects.get_for_model(Emp)
 view_permission1=Permission.objects.get(codename='view_blogpost',content_type=content_type1)
 view_permission2=Permission.objects.get(codename='view_author',content_type=content_type2)
 view_permission3=Permission.objects.get(codename='view_book',content_type=content_type3)
 view_permission4=Permission.objects.get(codename='view_emp',content_type=content_type4)
 group.permissions.add(view_permission1,view_permission2,view_permission3,view_permission4)

 from django.contrib.auth.models import Permission, Group, User
from django.contrib.contenttypes.models import ContentType
from myapp.models import Blogpost, Author, Book, Emp

# Get the group
from django.contrib.auth.models import Permission, Group, User
group = Group.objects.get(name="newgroup")

# Get the user
user = User.objects.get(username="Sujoy")

# Add the user to the group
user.groups.add(group)