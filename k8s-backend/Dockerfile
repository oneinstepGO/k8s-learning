# Use the official maven image to create a build artifact.
FROM maven:3.8.5-openjdk-17 AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package -DskipTests

# Second stage
FROM openjdk:17-jdk-slim
COPY --from=build /home/app/target/k8s-backend-0.0.1-SNAPSHOT.jar /usr/local/lib/k8s-backend.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/k8s-backend.jar"]