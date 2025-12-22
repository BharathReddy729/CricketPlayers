# Use Java 17 base image
FROM eclipse-temurin:21-jdk
 
# Set working directory inside container
WORKDIR /app
 
# Copy Spring Boot JAR into container
COPY target/*.jar app.jar
 
# Expose Spring Boot port
EXPOSE 8080
 
# Run the application
ENTRYPOINT ["java","-jar","app.jar"]
