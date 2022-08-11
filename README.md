# My OpenAPI Generator Test

README: [OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator#16---docker)
WebSite: [Generators List](https://openapi-generator.tech/docs/generators/)

## OpenAPI Generator Online

```bash
docker run -d -e GENERATOR_HOST=http://127.0.0.1 -p 80:8080 openapitools/openapi-generator-online:v6.0.1
```

Go to: http://localhost
Type in: `https://raw.githubusercontent.com/openapitools/openapi-generator/master/modules/openapi-generator/src/test/resources/3_0/petstore.yaml`

## OpenAPI Generator CLI

```bash
docker run --rm -v "${PWD}:/local" openapitools/openapi-generator-cli:v6.0.1 generate \
-g spring \
--library spring-boot \
-i  https://raw.githubusercontent.com/openapitools/openapi-generator/master/modules/openapi-generator/src/test/resources/3_0/petstore.yaml \
-o ${PWD} \
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