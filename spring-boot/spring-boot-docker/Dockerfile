FROM openjdk:11-slim-buster as build                         
COPY .mvn .mvn                                               
COPY mvnw .      
COPY pom.xml .                                               
COPY src src                                                 
RUN ./mvnw -B package                                        

FROM adoptopenjdk/openjdk11:alpine-jre
ARG JAR_FILE=target/*.jar
COPY --from=build ${JAR_FILE} application.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/application.jar"]
