# Étape 1 : Utilisation de Maven pour construire le fichier JAR
FROM maven:3.8.4-openjdk-17 AS builder
WORKDIR /app
COPY ./pom.xml ./
COPY ./src ./src
RUN mvn clean package -DskipTests

# Étape 2 : Création de l'image finale avec OpenJDK
FROM openjdk:17-jdk-alpine
WORKDIR /app
COPY --from=builder /app/target/*.jar eureka-server.jar
ENTRYPOINT ["java", "-jar", "/app/eureka-server.jar"]