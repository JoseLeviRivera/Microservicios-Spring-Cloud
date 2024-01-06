FROM maven:3.8.7-openjdk-12 AS builder

COPY pom.xml .

RUN mvn -e -B dependency:resolve

COPY src ./src

RUN mvn -e -B package -DskipTests

FROM openjdk:12-jre-slim

WORKDIR /app

COPY --from=builder target/shoold.jar app.jar

# Expone el puerto en el que se ejecutará tu aplicación Spring (ajusta según sea necesario)
EXPOSE 8085

ENTRYPOINT ["java", "-jar", "app.jar"]
