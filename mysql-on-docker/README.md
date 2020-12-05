# MySQL on Docker

### Process

1. MySQL 도커 이미지 다운로드

```sh
$ docker pull mysql
```

2. 도커 컨테이너 실행

```sh
$ docker run --name tutorial-db -e MYSQL_ROOT_PASSWORD=tutorialpw -d mysql
```

3. MySQL Client 접속

```sh
$ docker exec -it tutorial-db mysql -u root -p
```

4. MySQL Client Test

```sh
mysql> status
```

### Result

![mysql](https://user-images.githubusercontent.com/51071806/101245228-98795f80-374e-11eb-803d-942bdfa57fa3.png)

### References

- https://hub.docker.com/_/mysql
