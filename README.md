# ping-spring-boot
Ping project in Spring Boot

## Create the project
```bash
curl https://start.spring.io/starter.zip \
  -d type=maven-java \
  -d name=ping \
  -d groupId=cl.stringmachine \
  -d artifactId=ping \
  -d baseDir=ping-spring-boot \
  -o ping-spring-boot.zip
unzip ping-spring-boot.zip
rm ping-spring-boot.zip
cd ping-spring-boot
```

## Add controller
In `src/main/java/cl/stringmachine/ping/controller/PingController.java`:
```java
package cl.stringmachine.ping.controller;

import java.util.Map;

import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/ping")
public class PingController {

	@GetMapping("")
	public ResponseEntity<Map<String, String>> ping() {
		return ResponseEntity.ok(Map.of("message", "pong"));
	}

}
```

## Run the project
```bash
./mvnw spring-boot:run
```

## Test it
```bash
curl http://127.0.0.1:8080/ping
# Response: {"message":"pong"}
```
