FROM maven:3.9.16-eclipse-temurin-25-alpine as build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests # cancella prima tutto prendi tutto il package e salta i test

FROM eclipse-temurin:25-jre-jammy
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8887

ENTRYPOINT ["java", "-Dspring.profiles.active=${SPRING_PROFILE_ACTIVE:dev}", "-jar", "app.jar"]