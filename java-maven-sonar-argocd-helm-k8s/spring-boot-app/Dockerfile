########## 1️⃣ BUILD STAGE (Maven + Java 17) ##########
FROM maven:3.9-eclipse-temurin-17 AS build

WORKDIR /app

# Copy project files
COPY . .

# Build the JAR
RUN mvn clean package -DskipTests


########## 2️⃣ RUNTIME STAGE (Java 11 lightweight) ##########
FROM adoptopenjdk/openjdk11:alpine-jre

WORKDIR /opt/app

# Copy the JAR built in Stage 1
COPY --from=build /app/target/spring-boot-web.jar app.jar

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
