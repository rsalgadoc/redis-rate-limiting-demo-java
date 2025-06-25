# Build Stage
FROM gradle:7.6.5-jdk17 AS build
WORKDIR /app
COPY . .
RUN gradle build --no-daemon

# Runtime Stage
FROM amazoncorretto:17-alpine-jdk
WORKDIR /app
COPY --from=build /app/build/libs/*.jar app.jar
EXPOSE 5000 
ENTRYPOINT ["java", "-jar", "app.jar"]