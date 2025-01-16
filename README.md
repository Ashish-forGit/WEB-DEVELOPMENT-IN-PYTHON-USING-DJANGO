# WEB-DEVELOPMENT-IN-PYTHON-USING-DJANGO

# Django Setup
python -m venv myenv
myenv\Scripts\activate.bat
pip install django

# Project Setup
cd myenv
django-admin startproject myproject

# Run server
cd myproject
python manage.py runserver 

# Start Application
python manage.py startapp myapp