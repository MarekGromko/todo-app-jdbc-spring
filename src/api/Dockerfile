# building
FROM maven:3.9.12-eclipse-tumerin-17 as builder

WORKDIR /app

COPY pom.xml .
COPY ./src ./src

RUN mvn clean package -DskipTests

# running
FROM eclipse-temurin:17-jre-alpine

COPY -from=builder /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
