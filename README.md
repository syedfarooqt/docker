# docker

#sample java project to run as docker iamge
# Use the official OpenJDK image from Docker Hub
FROM openjdk:11-jdk-slim as builder

# Set the working directory inside the container
WORKDIR /app

# Copy the Spring Boot .jar file into the container
COPY target/SpringSecurity-0.0.1-SNAPSHOT.jar /app/app.jar

# Expose the port the app will run on (default Spring Boot port is 8080)
EXPOSE 9090

# Command to run the Spring Boot app
ENTRYPOINT ["java", "-jar", "/app/app.jar"]


#docker cmd to run and send image to others

 docker build -t spring-security-app .
 docker run -d -p 9090:9090 spring-security-app


 #to send and run docker in other system
  docker run -d -p 9090:9090 spring-security-app
  docker load -i spring-security-app.tar
  docker run -d -p 9090:9090 spring-security-app
