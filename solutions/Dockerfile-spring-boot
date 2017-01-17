FROM openjdk:jre-alpine
COPY ./build/libs/docker-example-0.0.1-SNAPSHOT.jar /usr/src/myapp/app.jar
WORKDIR /usr/src/myapp
EXPOSE 8080
CMD ["java", "-jar", "./app.jar"]
