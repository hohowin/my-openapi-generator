# My OpenAPI Generator Test

README: [OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator#16---docker)
WebSite: [Generators List](https://openapi-generator.tech/docs/generators/)

## OpenAPI Generator Online

```bash
docker run -d -e GENERATOR_HOST=http://127.0.0.1 -p 80:8080 openapitools/openapi-generator-online:v6.0.1
```

1. Go to: http://localhost
2. Type in: `https://raw.githubusercontent.com/openapitools/openapi-generator/master/modules/openapi-generator/src/test/resources/3_0/petstore.yaml`

## OpenAPI Generator CLI

- Youtube: [Introducing OpenAPI Generator](https://www.youtube.com/watch?v=t4jaTC7QjMg&t=286s)
- Blog: [OpenAPI generator](https://qiita.com/amuyikam/items/e8a45daae59c68be0fc8)

```bash
docker run --rm -v "${PWD}:/local" openapitools/openapi-generator-cli:v6.0.1 generate \
-g spring \
--library spring-boot \
-i  https://raw.githubusercontent.com/openapitools/openapi-generator/master/modules/openapi-generator/src/test/resources/3_0/petstore.yaml \
-o /local/out \
-p groupId=com.redhat \
-p artifactId=petstore \
-p artifactVersion=1.0.0-SNAPSHOT \
\
-p basePackage=com.redhat.petstore \
-p configPackage=com.redhat.petstore.config \
-p apiPackage=com.redhat.petstore.api \
-p modelPackage=com.redhat.petstore.model \
\
-p sourceFolder=src/main
```

Then in `pom.xml`, add plugin:

```json
<plugin>
    <groupId>org.codehaus.mojo</groupId>
    <artifactId>build-helper-maven-plugin</artifactId>
    <version>3.3.0</version>
    <executions>
        <execution>
            <phase>generate-sources</phase>
            <goals>
                <goal>add-source</goal>
            </goals>
            <configuration>
                <sources>src/main</sources>
            </configuration>
        </execution>
    </executions>
</plugin>
```

Then type:

```bash
mvn spring-boot:run
```

Then go to: http://localhost:8080