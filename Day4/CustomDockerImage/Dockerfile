FROM ubuntu:16.04

RUN apt update && apt install -y default-jdk

COPY spring-hello-1.0.jar ./app.jar 

CMD ["java","-jar","./app.jar"]
