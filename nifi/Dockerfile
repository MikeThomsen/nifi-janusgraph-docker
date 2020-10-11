FROM maven:3 AS build

COPY pom.xml /tmp/pom.xml

RUN mvn -f /tmp/pom.xml dependency:resolve

FROM apache/nifi:1.12.1

RUN ls -1 /opt/nifi/nifi-current/lib | wc -l

COPY --from=build /root/.m2/repository/org/apache/nifi/nifi-graph-client-service-api-nar/1.12.1/nifi-graph-client-service-api-nar-1.12.1.nar /opt/nifi/nifi-current/lib/nifi-graph-client-service-api-nar-1.12.1.nar
COPY --from=build /root/.m2/repository/org/apache/nifi/nifi-neo4j-cypher-service-nar/1.12.1/nifi-neo4j-cypher-service-nar-1.12.1.nar /opt/nifi/nifi-current/lib/nifi-neo4j-cypher-service-nar-1.12.1.nar
COPY --from=build /root/.m2/repository/org/apache/nifi/nifi-graph-nar/1.12.1/nifi-graph-nar-1.12.1.nar /opt/nifi/nifi-current/lib/nifi-graph-nar-1.12.1.nar
COPY --from=build /root/.m2/repository/org/apache/nifi/nifi-other-graph-services-nar/1.12.1/nifi-other-graph-services-nar-1.12.1.nar /opt/nifi/nifi-current/lib/nifi-other-graph-services-nar-1.12.1.nar


RUN ls -1 /opt/nifi/nifi-current/lib | wc -l
