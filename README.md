# Basic Microservices with Docker Compose

This repository contains a Docker Compose setup for running a simple microservices application with the following components:

- **Node.js Application**: A basic Node.js service.
- **Spring Boot Application**: A Spring Boot service connecting to PostgreSQL.
- **PostgreSQL Database**: A database for the Spring Boot application.

# Files in this Repo
- **docker-compose.yml**: The Docker Compose configuration for setting up all services. It pulls the necessary Dockerfiles, builds the images, and runs the services for Node.js, Spring Boot, and PostgreSQL.
- **Dockerfile (for Node.js)**: This Dockerfile uses a Node.js base image, installs dependencies, copies the application code, and exposes the service on port 8081.
- **Dockerfile (for Spring Boot)**: This Dockerfile uses a multi-stage build for better optimization. It first builds the Spring Boot app using Maven in one stage, then copies the resulting JAR file into a lightweight image and runs the Spring Boot application in the final image.

# How to Run the Application
# Clone the repository:
   
  git clone https://github.com/Edin9898/basic-microservices.git
   
# Navigate to the project directory:

  cd basic-microservices

# Build and start the services with Docker Compose:

  docker-compose up --build

# Once all services (containers) are running, you can test if the services are working properly by running the following command locally:

  bash <(curl -s https://raw.githubusercontent.com/kkenan/basic-microservices/master/health_check.sh)

# If everything is set up correctly, you should see the output: All checks passed. Congrats!
