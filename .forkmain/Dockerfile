##
## Build
##
FROM openjdk:8 AS builder

WORKDIR /workdir

COPY ./ ./

RUN ./gradlew build && cp "build/libs/*.jar build/libs/app.jar

##
## Run
##
FROM openjdk:18

WORKDIR /workdir

COPY --from=builder /workdir/build/libs/ ./

EXPOSE 9080

CMD ["sh", "-c", "java -jar app.jar"]
