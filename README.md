# 🦁 Spring @Controller and @RestController annotations
## 1.Overview
Today, we'll discuss briefly the difference between @Controller and @RestController annotations in Spring MVC.

We can use the first annotation for traditional Spring controllers, and it has been part of the framework for a very long time.

Spring 4.0 introduced the @RestController annotation in order to simplify the creation of RESTful web services. It's a convenient annotation that combines @Controller and @ResponseBody, which eliminates the need to annotate every requrest handling method of the controller class with the @Response Body annotation.

## 2. Spring MVC @Controller
We can annotate classic controller with the @Controller annotation. This is simply a specialization of the @Component class, which allows us to auto-detect implementation classes through the classpath scanning.

We typically use @Controller in combination with a @RequestMapping annotation for request handling methods.

A quick example of the Spring MVC controller

```java
@Controller
@RequestMapping("books")
public class SimpleBookController {
  @GetMapping("/{id}", produces = "application/json")
  public @ResponseBody Book getBook(@PathVariable int id){
    return findBookById(id);
  }

  private Book findBookById(int id){
    //...
  }
}
```

We annonated the request handling method with @ResponseBody. This annotation enables automatic serialization of the return object into the HttpResponse.

## 3. Spring MVC @RestController
@RestController is a specialized version of the controller. It includes the @Controller and @ResponseBody annotations, and as a result, simplifies the controller implementation:

```java
@RestController
@RequestMapping("books-rest")
public class SimpleBooksController {
  @GetMapping("/{id}", produces = "application/json")
  public Book getBook(@PathVariable int id){
    return findBookById(id);
  }
  private Book findBookById(int id){
    // ...
  }
}
```

Here, the controller is annotated with the @RestController annotation; therefore, the @ResponseBody isn't required.

Every request handling method of the controller class automatically serializes return objects into ***HttpResponse***

























