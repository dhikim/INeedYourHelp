FROM gradle:7.6.0-jdk8 AS BUILD

ENV TZ=Asia/Seoul
COPY --chown=gradle:gradle . /home/gradle/src
WORKDIR /home/gradle/src
RUN gradle build --no-daemon

FROM openjdk:8-jdk-alpine

RUN mkdir /app
RUN mkdir /var/log/spring

WORKDIR /app
COPY --from=BUILD /home/gradle/src/build/libs/beakgu-0.0.1-SNAPSHOT.jar .
