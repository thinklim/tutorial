# Django Starter App with Docker Tutorial

### Process

1. 도커 이미지 생성

```sh
$ docker build -t tutorial .
```

2. 도커 컨테이너 실행

```sh
$ docker run -i -p 8000:8000 tutorial
```

3. 브라우저 접속

```sh
127.0.0.1:8000
```

### Result

- ![django-starter-view](https://user-images.githubusercontent.com/51071806/100499276-8f671c00-31ab-11eb-9cb7-1f31c529ccee.png)
