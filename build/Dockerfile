FROM yan234280533/sample-app:v2-0
MAINTAINER devinyan <devinyan@tencent.com>

ENV JAVA_HOME              /usr/lib/jvm/java-8-openjdk-amd64
ENV JAVA_OPTS              ""
ENV PATH                   $JAVA_HOME/bin:$PATH

ENV TIME_ZONE              Europe/Budapest
ENV SPRING_PROFILES_ACTIVE test

RUN echo "$TIME_ZONE" > /etc/timezone
RUN dpkg-reconfigure -f noninteractive tzdata

ADD pom.xml /source/pom.xml
ADD src /source/src
RUN cd /source && mvn -X clean package && mkdir -p /app && cp ./target/app.jar /app/app.jar

WORKDIR /app

EXPOSE 8080

CMD ["/bin/sh", "-c", "java $JAVA_OPTS -jar /app/app.jar --spring.profiles.active=$SPRING_PROFILES_ACTIVE"]



