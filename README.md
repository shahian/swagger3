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
##2. Create OpenAPI Configuration File
```
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


