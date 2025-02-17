# Step 1: Use Maven to build the application
FROM maven:3.8.7-openjdk-18-slim AS builder

# Install git
RUN apt-get update && apt-get install -y git

# Set working directory
WORKDIR /app

# Clone the repository
RUN git clone https://github.com/kkenan/basic-microservices.git .

# Navigate to the Spring Boot app directory
WORKDIR /app/spring-boot-app

# Build the application using Maven
RUN mvn clean package

# Step 2: Use a lightweight image to run the application
FROM openjdk:8-jre-alpine

# Set working directory in the final image
WORKDIR /app

# Copy the built JAR file from the previous stage
COPY --from=builder /app/spring-boot-app/target/spring-boot-app-1.0-SNAPSHOT.jar app.jar

# Copy the application.yml from the repo to the standard Spring Boot config location
COPY --from=builder /app/spring-boot-app/src/main/resources/application.yml /config/application.yml

# Expose the application port
EXPOSE 8080

# Command to run the application
CMD ["java", "-jar", "app.jar"]
