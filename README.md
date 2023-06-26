# Enable OpenAPI 3(Swagger) in Spring Boot 3
OpenAPI (formerly known as Swagger) is a specification for building and documenting RESTful APIs. It allows developers to describe their API operations, inputs, outputs, and other aspects in a structured and machine-readable format. This documentation can then be used by developers and users to understand and interact with the API.

In Spring Boot applications, OpenAPI can be used to automatically generate documentation for your REST APIs. By using annotations provided by libraries like Springdoc OpenAPI, you can document your APIs in a way that can be easily parsed and displayed by the OpenAPI specification.

##1. Add OpenAPI Maven Dependency
To enable the generation of API documentation, we need to add a springdoc-openapi-starter-webmvc-ui dependency to our Spring Boot project.

```
<!-- https://mvnrepository.com/artifact/org.springdoc/springdoc-openapi-starter-webmvc-ui -->
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
    <version>2.0.2</version>
</dependency>
```
## 2. Create OpenAPI Configuration File
```
package com.shahian.swagger3;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import io.swagger.v3.oas.models.OpenAPI;
import io.swagger.v3.oas.models.info.Info;

@Configuration
public class OpenApiConfig {

    @Bean
    public OpenAPI usersMicroserviceOpenAPI() {
        return new OpenAPI()
                .info(new Info().title("Your API Title")
                                 .description("Your API Description")
                                 .version("1.0"));
    }
}
```
The code above is a configuration class that sets up OpenAPI (formerly known as Swagger) documentation for your Spring Boot 3 application.

The @Configuration annotation on the OpenApiConfig class tells Spring to treat this class as a configuration class, which means that it will be used to configure various aspects of your application.

The @Bean annotation on the usersMicroserviceOpenAPI() method indicates that this method will return an instance of the OpenAPI object, which is used to define the OpenAPI documentation for your application.

The new OpenAPI() statement creates a new instance of the OpenAPI class, which is the main class used for setting up OpenAPI documentation.

The .info(new Info().title("Your API Title").description("Your API Description").version("1.0")) method chain sets the basic information about your API, including its title, description, and version.

## 3. Open API Configuration Properties for Spring Boot 3

```
# Specify the path of the OpenAPI documentation
springdoc.api-docs.path=/api-docs
# Specify the path of the Swagger UI
springdoc.swagger-ui.path=/swagger-ui.html
# Enable or disable Swagger UI
springdoc.swagger-ui.enabled=true
```
In a Spring Boot 3 application that uses OpenAPI (formerly known as Swagger), the following configuration properties are used to specify the path and enable/disable the Swagger UI:

springdoc.api-docs.path=/api-docs: This property specifies the URL path for the OpenAPI documentation generated by Springdoc OpenAPI. By default, the OpenAPI documentation will be available at http://<hostname>:<port>/<context-path>/api-docs.

springdoc.swagger-ui.path=/swagger-ui.html: This property specifies the URL path for the Swagger UI. The Swagger UI is a web-based UI for interacting with your API documentation, and it is generated automatically by Springdoc OpenAPI. By default, the Swagger UI will be available at http://<hostname>:<port>/<context-path>/swagger-ui.html.

springdoc.swagger-ui.enabled=true: This property enables or disables the Swagger UI. By default, the Swagger UI is enabled and can be accessed at the URL specified by springdoc.swagger-ui.path.

So, if you set springdoc.swagger-ui.enabled=false, then the Swagger UI will be disabled, and users will not be able to access it. This can be useful if you don’t want to expose the Swagger UI in your production environment.

## 4. Create a simple Rest Controller class
```
package com.shahian.swagger3.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api")
public class TestController {
    @GetMapping("v1/test")
    public String getTest(){
        return "this is a test api for swagger";
    }
}
```

