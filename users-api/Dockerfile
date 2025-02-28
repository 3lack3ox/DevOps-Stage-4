# Stage 1: Build the Spring Boot application
FROM maven:3.8-openjdk-8 AS builder

# Set the working directory for the build process
WORKDIR /app

# Copy the application files to the container
COPY . .

# Build the Spring Boot application (skip tests for faster builds)
RUN mvn clean package -DskipTests

# Stage 2: Create a minimal runtime container
FROM openjdk:8-jre-alpine

# Set the working directory for the runtime environment
WORKDIR /app

# Copy the JAR file from the builder stage
COPY --from=builder /app/target/users-api-0.0.1-SNAPSHOT.jar /app/users-api.jar

# Expose the application's port
EXPOSE 8083

# Run the Spring Boot application
CMD ["java", "-jar", "/app/users-api.jar"]

