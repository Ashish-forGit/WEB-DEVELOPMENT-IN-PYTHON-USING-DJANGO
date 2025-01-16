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



