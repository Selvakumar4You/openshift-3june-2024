FROM registry.redhat.io/ubi8/openjdk-11:latest as builder
MAINTAINER Jeganathan Swaminathan <jegan@tektutor.org>

RUN mkdir -p -m 0700 ./hello/target
WORKDIR ./hello

COPY . ./ 
RUN mvn package && cp ./target/spring-hello-1.0.jar /tmp/app.jar

FROM registry.redhat.io/ubi8/openjdk-11:latest as runner

COPY --from=builder /tmp/app.jar .
CMD ["java", "-jar", "./app.jar"]
