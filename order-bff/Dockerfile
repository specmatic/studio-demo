FROM alpine:3.22

RUN apk add --no-cache openjdk17-jdk git curl bash && \
    rm -rf /var/cache/apk/*

RUN git clone https://github.com/specmatic/specmatic-order-bff-java /app

WORKDIR /app

EXPOSE 9092
EXPOSE 2181

RUN ./gradlew clean assemble --no-daemon

CMD java -jar build/libs/specmatic-order-bff-java-1.0-SNAPSHOT.jar
