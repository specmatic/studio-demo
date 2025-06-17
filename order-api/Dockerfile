FROM alpine:3.22

RUN apk add --no-cache openjdk17-jdk git curl bash && \
    rm -rf /var/cache/apk/*

RUN git clone https://github.com/specmatic/specmatic-order-api-java /app

WORKDIR /app

EXPOSE 8090

RUN ./mvnw clean package -DskipTests

CMD java -jar target/specmatic-order-api-1.0-SNAPSHOT.jar
