FROM registry.access.redhat.com/ubi8/ubi-minimal AS builder

RUN microdnf -y install java-11-openjdk-devel

RUN mkdir /build
RUN curl -sL https://repo1.maven.org/maven2/com/h2database/h2/1.4.200/h2-1.4.200.jar -o /build/h2.jar

ADD src /source
RUN jar -cvf /build/h2-extension.jar -C /source .

FROM registry.access.redhat.com/ubi8/ubi-minimal

RUN mkdir /build

COPY --from=builder /build/* /build/
RUN ls /build

CMD ["bash", "-ec", "ls / && cp -v /build/*.jar /ext/ && ls /ext/"]
