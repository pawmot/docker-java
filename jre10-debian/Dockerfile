FROM debian:9-slim
LABEL maintainer="Paweł Motyl <pawmot@gmail.com>" 

RUN apt-get update
RUN apt-get install -y -qq wget

ENV JAVA_VERSION=10

RUN cd /tmp && \
    wget --header "Cookie: oraclelicense=accept-securebackup-cookie;" "http://download.oracle.com/otn-pub/java/jdk/10.0.1+10/fb4372174a714e6b8c52526dc134031e/serverjre-10.0.1_linux-x64_bin.tar.gz"
RUN tar -xzf "/tmp/serverjre-10.0.1_linux-x64_bin.tar.gz"

FROM debian:9-slim

ENV JAVA_VERSION=9
ENV JAVA_HOME="/usr/lib/jvm/default-jvm"

RUN mkdir -p "/usr/lib/jvm"
COPY --from=0 "/jdk-10.0.1" "/usr/lib/jvm/java-${JAVA_VERSION}-oracle"
RUN ln -s "/usr/lib/jvm/java-${JAVA_VERSION}-oracle" "$JAVA_HOME" && \
    ln -s "$JAVA_HOME/bin/"* "/usr/bin/"

CMD ["java", "-version"]
