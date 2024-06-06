FROM docker.io/maven:3.6.3-jdk-11 as stage1
COPY . .
RUN mvn clean package

FROM registry.access.redhat.com/ubi8/openjdk-11
COPY --from=stage1 target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT [ "java", "-jar", "app.jar" ]
