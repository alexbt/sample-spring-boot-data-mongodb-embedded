Spring Boot, Spring Data MongoDB and Embedded MongoDB
---------------------------------------------------

In almost all of my projects that involves external resources, I try my best to enable the application to fully run without dependencies.
It's useful to provide a fully working backing 
This sample project shows how a spring-boot application can be setup with an embedded MongoDB.
The focus of this project is to show how to configure an embedded database with Spring Boot, however the source code also contains a RestController and a Spring Data Repository.



Other sample projects with embedded databases 
---------------------------------------------------
* [sample-spring-boot-data-mongodb-embedded](https://github.com/alexturcot/sample-spring-boot-data-mongodb-embedded)
* [sample-spring-boot-data-mongodb-embedded-multiple](https://github.com/alexturcot/sample-spring-boot-data-mongodb-embedded-multiple)
* [sample-spring-boot-data-solr-embedded](https://github.com/alexturcot/sample-spring-boot-data-solr-embedded)
* [sample-spring-boot-data-redis-embedded](https://github.com/alexturcot/sample-spring-boot-data-redis-embedded)
* [sample-spring-boot-data-keyvalue-embedded](https://github.com/alexturcot/sample-spring-boot-data-keyvalue-embedded)
* [sample-spring-boot-data-jpa-embedded](https://github.com/alexturcot/sample-spring-boot-data-jpa-embedded)


Step by step
---------------------------------------------------

**Maven dependencies**
To load an embedded MongoDB with Spring Boot, all you need is to add its maven dependency into your pom. The rest will be taken care of. MongoDB binaries will even be downloaded on the fly at build time.

```
<dependency>
    <groupId>de.flapdoodle.embed</groupId>
    <artifactId>de.flapdoodle.embed.mongo</artifactId>
    <version>1.50.5</version>
</dependency>

<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-mongodb</artifactId>
</dependency>
```

**Spring Boot configuration**
Absolutely no configuration is required. By default, the embedded database will be started with url ```mongodb://localhost:27017/test```
Spring Boot's EmbeddedMongoAutoConfiguration, the embedded database will be detected and a datasource pointing to it will be created.

If you have a mongo client installed you may access it normally:

    $ mongo localhost:27017/test
    $ show collections
    
For now, your mongo instance is probably empty since you have not yet added anything. Setup a Spring Data MongoRepository, start adding collections or do it from the command line:

    $ db.yourcollection.insertOne({"field":"value"})

**That's it**

Assuming you have a Spring Boot entry point, launch it:
```
@SpringBootApplication
public class Launcher {
    
    public static void main(String[] args){
        new SpringApplicationBuilder() //
        .sources(Launcher.class)//
        .run(args);
    }
}
```

Get the code - do it
------------------------
Clone the repository:

    $ git clone https://github.com/alexturcot/sample-spring-boot-data-mongodb-embedded.git