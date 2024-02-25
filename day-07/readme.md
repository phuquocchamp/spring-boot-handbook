### 200 DAYS TO BECOME A JAVA DEV | DAY 07/200.

#### SPRING BOOT ACTUATOR

##### Tutorial Guider

![1708674977340](image/readme/1708674977340.png)

**Config application.properties**

```properties
management.endpoints.web.exposure.include=*
```

> properties trên dùng để config spring boot actuator .

###### /info

![1708675539423](image/readme/1708675539423.png)

**Config**

> management.info.env.enabled=true dùng để enable info actuator.

```properties
management.info.env.enabled=true

info.app.name = Spring Boot RestApi Webservices
info.app.description = This is a RestApi Webservices
info.app.version = 1.0

```

**Output**

![1708676736922](image/readme/1708676736922.png)

###### /health

![1708676185252](image/readme/1708676185252.png)

**Config**

```properties
# /health config
management.endpoint.health.show-details=always

```

**Output**

![1708676777361](image/readme/1708676777361.png)

###### /bean

![1708676837905](image/readme/1708676837905.png)

###### /conditions

![1708676986334](image/readme/1708676986334.png)

###### /mappings

![1708677072528](image/readme/1708677072528.png)

###### /configprops

![1708677118691](image/readme/1708677118691.png)

###### /matrics

![1708677161009](image/readme/1708677161009.png)

###### /env

![1708677215093](image/readme/1708677215093.png)

###### /loggers

![1708677256850](image/readme/1708677256850.png)

###### /shutdown

![1708677306840](image/readme/1708677306840.png)

#### RESTAPI DOCMENTATION

[RESTful API Document Tạo với Spring Boot + Swagger](https://loda.me/articles/sb24-restful-api-document-tao-voi-spring-boot-swagger)

##### Tutoial Guider

![1708677506740](image/readme/1708677506740.png)

![1708677612498](image/readme/1708677612498.png)

###### Define General API Information

> Add this annotation in spring boot app

```properties
@OpenAPIDefinition(
        info = @Info(
                title = "Spring Boot REST API Documentation",
                description = "Spring Boot REST API Documentation",
                version = "v1.0",
                contact = @Contact(
                        name = "phuquocchamp",
                        email = "phuquocchamp@gmail.com",
                        url = "phuquoccchamp.blogs.vn"
                ),
                license = @License(
                        name = "Apache 2.0",
                        url = "phuquochamp.blogs.vn"
                )
        ),
        externalDocs = @ExternalDocumentation(
                description = "Spring Boot User Management Documentation",
                url = "https://github.com/phuquocchamp/spring-boot-handbook"
        )
)
```

![1708694806148](image/readme/1708694806148.png)

###### Customize Swagger API Document

**Config**

![1708695756136](image/readme/1708695756136.png)

**Output**

![1708695711084](image/readme/1708695711084.png)

#### TODO MANAGEMENT PROJECT

##### Requirement 1

![1708695839338](image/readme/1708695839338.png)

###### Database Config

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/todo_management
spring.datasource.username=testuser
spring.datasource.password=user@12345
spring.jpa.hibernate.ddl-auto=update

spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQLDialect

spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

```

> **Trong spring.jpa.hibernate.ddl-auto=?**

- none: The default for MySQL. We make no change to the database structure.
- update: Hibernate changes the database according to the entity structures.
- create: Creates the database every time but does not drop it on close.
- create-drop: Creates the database and drops it when SessionFactory closes.

> **spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQLDialect ?**

-> The SQL dialect makes Hibernate generate better SQL for the chosen database

##### Requirement 2

![1708695867454](image/readme/1708695867454.png)

![1708695907148](image/readme/1708695907148.png)
