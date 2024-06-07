FROM registry.access.redhat.com/ubi8/openjdk-17 as builder
RUN mkdir -p /home/jboss/myproject/target
WORKDIR /home/jboss/myproject
COPY pom.xml .
COPY src .
RUN mvn clean package

FROM registry.access.redhat.com/ubi8/openjdk-17
COPY --from=builder target/hello-1.0.0.jar app.jar
EXPOSE 8080
ENTRYPOINT [ "java", "-jar", "app.jar" ]
