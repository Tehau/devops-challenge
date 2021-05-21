FROM openjdk:8-jdk-alpine

ARG JAR_FILE=target/*.jar

COPY ${JAR_FILE} app.jar

RUN addgroup -S app && adduser -S app -G app

USER app:app

EXPOSE 8080

ENTRYPOINT ["java","-jar","/app.jar"]