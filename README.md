# Weather Forecast Application

## Table of Contents

- [Prerequisite](#Prerequisite)
- [Setup](#Setup)
- [Features](#features)
- [Demo](#Demo)


---

## Prerequisite

- All the `code` required to get started

- Install `Redis` or use my `Redis` at cloud (checkout the configuration at `application-cloud.properties`)
> https://redis.io/download
>
```shell 
spring.datasource.url=jdbc:mysql://18.141.220.149:3306/weatherapp?characterEncoding=UTF-8
spring.datasource.username=user1
spring.datasource.password=Qwe123!@#
```

- Install `MySQL` or use my `MySQL` at cloud (checkout the configuration at `application-cloud.properties`)
> https://dev.mysql.com/downloads/
>
```$xslt 
spring.redis.host=18.141.220.149
spring.redis.port=6379
spring.redis.password=
spring.redis.database=1
```

- Install lombok plugin to your IDE 
> Eclipse: https://projectlombok.org/setup/eclipse

> IntelliJ: install lombok at `Preferences | Plugins` 

### Setup

- update and install dependencies first

```shell
$ mvn clean install
```
- run 

```shell
$ mvn spring-boot:run
```

- run unit test

```shell
$ mvn test
```

- build docker image
```shell
    docker build -t weatherapp:1.0 .
```
- run docker 
```$xslt
    docker run -p 8080:8080 -d --name weatherapp weatherapp:1.0 
```
---

## Features
- Search current weather based on city by consuming this api: `https://openweathermap.org/api`
> Returned data from 3rd API will be cached by `Redis` for faster access later
>
> Returned data from 3rd API will be stored in `MySQL` for archiving purposes.
>This task will be executed in background by using `Task Queue` of `Redis`
- Fetch the past weather logs based on city
- Retrieve weather logs by different criteria (`city`, `start date`, `end date`) 
- Delete the weather logs
- Download the weather logs  

---

## Dependencies
- `Spring Boot` Build Web Page + REST API
- `Spring Data JPA + Hibernate` Manage data in database
- `Spring Data Redis` Cache data in memory
- `Model Mapper` Map Model Object
- `RQueue` Task executor backed by Redis Task Queue
- `Swagger` Generate API document
- `Lombok` Generate Setter / Getter / Constructor for class
- `JUnit` Run Unit test
---

## Demo
- Try this project at this site
> http://oddleweatherapp-env.eba-gfm8d55m.ap-southeast-1.elasticbeanstalk.com/
- API Documentation
> http://oddleweatherapp-env.eba-gfm8d55m.ap-southeast-1.elasticbeanstalk.com/swagger-ui.html
---
