FROM openjdk:16-jdk-alpine
RUN addgroup -S spring && adduser -S spring -G spring
USER spring:spring
ENV JAVA_OPTS "-Xms256m -Xmx512m -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9010 -Dcom.sun.management.jmxremote.rmi.port=9010 -Dcom.sun.management.jmxremote.local.only=false -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -javaagent:./jmx_prometheus_exporter.jar=9404:config.yaml"
ARG JAR_FILE
ARG JMX_EXPORTER_JAR
ARG JMX_EXPORTER_CONFIG
COPY ${JAR_FILE} /app.jar
COPY ${JMX_EXPORTER_JAR} /jmx_prometheus_exporter.jar
COPY ${JMX_EXPORTER_CONFIG} /config.yaml
ENTRYPOINT ["sh", "-c", "java ${JAVA_OPTS} -jar /app.jar"]