# ---- Étape 1 : Build ----
FROM eclipse-temurin:21-jdk-alpine AS build
WORKDIR /opt/app
RUN apk add --no-cache maven
COPY pom.xml .
RUN mvn -q -DskipTests dependency:go-offline
COPY src ./src
RUN mvn -q -DskipTests package

# ---- Étape 2 : Run ----
FROM eclipse-temurin:21-jre-alpine
ENV MYAPP_HOME=/opt/myapp
WORKDIR $MYAPP_HOME
COPY --from=build /opt/app/target/*.jar $MYAPP_HOME/app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
