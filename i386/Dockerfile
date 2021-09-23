FROM i386/ubuntu:18.04 AS base-ubuntu
RUN apt-get update && apt-get install -y --no-install-recommends git tzdata glibc-source libssl-dev openssl ca-certificates openjdk-11-jre-headless && rm -rf /var/lib/apt/lists/*
RUN echo 'root:1234' | chpasswd

FROM adoptopenjdk/openjdk11:alpine AS jdk
WORKDIR /app
COPY ./HelloWorld.java .
RUN javac HelloWorld.java

FROM base-ubuntu
WORKDIR /tmp
COPY --from=jdk /app .
CMD ["java", "HelloWorld"]
