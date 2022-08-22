FROM openjdk:11-slim-buster as build                         
COPY .mvn .mvn                                               
COPY mvnw .                                                  
COPY src src                                                 
RUN ./mvnw -B package                                        



FROM adoptopenjdk/openjdk11:alpine-jre
RUN ./mvnw clean install
RUN ./mvnw spring-boot:build-image
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} application.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/application.jar"]
