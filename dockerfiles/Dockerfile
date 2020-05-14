FROM adoptopenjdk/openjdk11-openj9:jdk-11.0.1.13-alpine-slim
COPY service.jar service.jar
RUN addgroup -g 1001 -S appuser && adduser -u 1001 -S appuser -g appuser
RUN chown -R appuser:appuser /opt/
RUN mkdir /opt/logs && chown -R appuser:appuser /opt/logs/
USER appuser
EXPOSE 8080
CMD java -XX:+UnlockExperimentalVMOptions -XX:+UseCGroupMemoryLimitForHeap -Dcom.sun.management.jmxremote -noverify ${JAVA_OPTS} -jar service.jar
