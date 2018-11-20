# Spring CheatSheet for FISE3

## Preliminary notes
* UPPERCASE = where to put annotation
* {XXX} = generally applies to XXX

## HTTP verbs
* GET: gets a "document"
* POST: sends a "document"
* UPDATE: modifies a "document"
* DELETE: removes a "document"

## Configuration File
* `src/resources/application.properties`
  ```server.port=<Tomcat listening port>```

## Spring Persistence (JPA)
* Configuration file src/resources/application.properties
  ```
   spring.jpa.hibernate.ddl-auto=<none, update, create, create-drop>
   spring.datasource.url=jdbc:mysql://localhost:port/db
   spring.datasource.username=<user>
   spring.datasource.password=<pass>
   ```
* CLASS @Entity: signals that the class has to be persisted
* CLASS @Table("table_name"): sets the name of the DB table if it cannot be deduced from the class name
* CLASS @NamedQuery: define you own queries
* ATTRIBUTE @Id: signals the attribute is used as a primary key in the DB
* ATTRIBUTE @GeneratedValue(GenerationType.{TABLE,SEQUENCE,IDENTITY,AUTO) [@Id]: specifies the way the DB to generates the numbers
* ATTRIBUTE @JoinColumn("col_name") [@OneToMany]:  provides the name of the column(s) used in this class' DB to ID/point to the element
* ATTRIBUTE @OneToMany/@ManyToOne/@ManyToMany: specifies the direction(s) when a relation between 2 objects is multiple
* ATTRIBUTE @Transient: marks an attribute that does not need to be persisted
* ATTRIBUTE @Column("name"): sets the name of the column in the DB table if it cannot be deduced from the attribute name 
* `findBy<AttributeName>()`: Spring automagically creates these methods to find objects according to the value of any of their attributes

## Application
* CLASS @SpringBootApplication
* @SpringBootApplication = @Configuration + @EnableAutoConfiguration + @ComponentScan
* METHOD main:
  ```java
  public static void main(String[] args) { SpringApplication.run(MyClass.class, args); }
  ```

## Controllers
* CLASS @Controller (presentation layer)
* CLASS @RestController = @Controller + @ResponseBody
* METHOD @GetMapping("/path"): indicates what URL will execute this method
* METHOD @RequestMapping {@RestController}: indicates what URL will execute this method RESTful for a service

## Repositories
* CLASS @Repository (persistence layer)
* @RepositoryRestResource:
  * collectionResourceRel: rel value to use when generating links to this resource
  * path where (URL) this resource is exported
  
# External Resources

* http://files.zeroturnaround.com/pdf/zt_spring_annotations_cheat_sheet.pdf
* https://www.cheatography.com/danielfc/cheat-sheets/spring-framework-4/
* https://github.com/LaunchCodeEducation/cheatsheets/tree/master/spring-persistence
* https://dzone.com/storage/assets/4082-rc026-springannot_online.pdf
* https://www.baeldung.com/spring-boot
* https://www.youtube.com/watch?v=MDdA53nrgLo
