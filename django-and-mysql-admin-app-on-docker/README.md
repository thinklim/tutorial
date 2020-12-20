# Django and MySQL Admin App on Docker

### Process

1. Database Volumes 폴더 생성

```sh
$ mkdir <path>/db-data
```

2. 도커 컴포즈로 초기 Django Project 생성

```sh
$ docker-compose run web django-admin startproject config .
```

3.  초기 Django Project 파일 소유를 Root 소유에서 유저 소유로 변경

```sh
$user sudo chown -R $USER:$USER .
```

4. Django에서 MySQL을 연결하기 위해 config/settings.py 변경

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'tutorialdb',
        'USER': 'tutorial',
        'PASSWORD': 'tutorialpw',
        'HOST': 'db',
        'PORT': 3306
    }
}
```

5.  도커 컴포즈 백그라운드로 실행(Django app 실행, 이미 MySQL Server는 실행 중)

```sh
$ docker-compose up -d
```

6.  초기 Django 데이터베이스 테이블 생성

```sh
$ docker-compose exec web python manage.py migrate
```

7.  Django Admin 계정 생성

```sh
$ docker-compose exec web python manage.py createsuperuser
```

8.  Django Admin 페이지 접속

```sh
http://localhost:9000/admin/
```

### Result

Django Admin Page:
![django-admin-page-view](https://user-images.githubusercontent.com/51071806/102714166-24bf8100-4310-11eb-998d-e42ac1a6dfd5.png)

MySQL Server:

```sh
docker exec -it <mysql container> mysql -u tutorial -p
```

![django-mysql-view](https://user-images.githubusercontent.com/51071806/102714331-263d7900-4311-11eb-8bc1-5277b20caf3c.png)

### References

- https://docs.docker.com/compose/django/
- https://hub.docker.com/_/mysql
- https://djangoforprofessionals.com/
  - https://djangoforprofessionals.com/introduction/
  - https://djangoforprofessionals.com/docker/
  - https://djangoforprofessionals.com/postgresql/
