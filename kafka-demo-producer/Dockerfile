#
# Build stage
#
FROM registry.access.redhat.com/ubi8/openjdk-11:1.14-3 AS build
USER root
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package 

FROM registry.access.redhat.com/ubi8/openjdk-11:1.14-3
COPY --from=build /home/app/target/kafka-demo-producer-0.1.jar /usr/local/lib/kafka-demo-producer-0.1.jar

EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/kafka-demo-producer-0.1.jar"]
