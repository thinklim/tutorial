FROM python:3
ENV PYTHONUNBUFFERED=1
WORKDIR /tutorial
COPY requirements.txt /tutorial/
RUN pip install -r requirements.txt

# Django creating a project
RUN django-admin startproject config .

# Django app run
CMD python manage.py runserver 0.0.0.0:8000
