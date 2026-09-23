FROM apache/kafka:4.0.2

ADD --chown=appuser:appuser \
  https://linkedin.jfrog.io/artifactory/cruise-control/com/linkedin/cruisecontrol/cruise-control-metrics-reporter/2.5.146/cruise-control-metrics-reporter-2.5.146.jar \
  /opt/kafka/libs/cruise-control-metrics-reporter-2.5.146.jar

RUN chown appuser:appuser /opt/kafka/libs/*.jar
