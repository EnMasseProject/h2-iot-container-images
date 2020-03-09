FROM registry.access.redhat.com/ubi8/ubi-minimal

RUN microdnf -y install java-11-openjdk-headless
RUN curl -sL https://repo1.maven.org/maven2/com/h2database/h2/1.4.200/h2-1.4.200.jar -o h2.jar

ENV H2_TCP_PASSWORD "seriously-change-me"

ENTRYPOINT java -cp h2.jar org.h2.tools.Server -tcp -baseDir /data -ifExists -tcpAllowOthers -tcpPassword "${H2_TCP_PASSWORD}"
