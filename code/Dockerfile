FROM maven:3.8.2-openjdk-8

RUN mkdir -p /usr/app
WORKDIR /usr/app
COPY src ./src
COPY pom.xml ./pom.xml
COPY settings.xml /usr/share/maven/conf/settings.xml
RUN mvn package

FROM maven:3.8.2-openjdk-8
RUN mkdir -p /usr/app
WORKDIR /usr/app
COPY --from=0 /usr/app/target/demo-0.1.0.jar  /usr/app/demo.jar
ENTRYPOINT ["java", "-jar", "demo.jar"]
