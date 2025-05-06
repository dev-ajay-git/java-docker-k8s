# Stage 1: Build the Java Application
FROM maven:3.8.1-jdk-11-slim AS build

WORKDIR /app

COPY pom.xml /app/
COPY src /app/src

RUN mvn clean install

# Stage 2: Create a clean image with the WAR file
FROM tomcat:9.0-jdk11-openjdk-slim

WORKDIR /usr/local/tomcat

COPY --from=build /app/target/java-docker-k8s.war /usr/local/tomcat/webapps/

EXPOSE 8080

CMD ["catalina.sh", "run"]

