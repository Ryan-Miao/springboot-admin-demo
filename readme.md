Spring-boot-admin项目健康监控
====

我们知道spring-boot-actor暴露了大量统计和监控信息的端点，spring-boot-admin
就是为此提供的监控项目。


## server端

```xml
  <dependencyManagement>
    <dependencies>
      <dependency>
        <groupId>de.codecentric</groupId>
        <artifactId>spring-boot-admin-dependencies</artifactId>
        <version>${spring-boot-admin.version}</version>
        <type>pom</type>
        <scope>import</scope>
      </dependency>
    </dependencies>
  </dependencyManagement>
  
    <dependencies>
      <dependency>
        <groupId>de.codecentric</groupId>
        <artifactId>spring-boot-admin-starter-server</artifactId>
      </dependency>
      <dependency>
        <groupId>de.codecentric</groupId>
        <artifactId>spring-boot-admin-server-ui</artifactId>
      </dependency>
    </dependencies>
```

在启动类上添加`@EnableAdminServer`



## client 端

```xml
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>
    <dependency>
      <groupId>de.codecentric</groupId>
      <artifactId>spring-boot-admin-starter-client</artifactId>
    </dependency>


  <build>
    <plugins>
      <plugin>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-maven-plugin</artifactId>
        <version>${springboot.version}</version>
        <executions>
          <execution>
            <goals>
              <goal>build-info</goal>
            </goals>
          </execution>
        </executions>
      </plugin>

    </plugins>
  </build>
```


client端添加admin的url
```xml
spring:
  boot:
    admin:
      url: http://localhost:8081
management:
  security:
    enabled: false
```

