FROM debian:9-slim
LABEL maintainer="Paweł Motyl <pawmot@gmail.com>" 

RUN apt-get update
RUN apt-get install -y -qq wget

ENV JAVA_VERSION=9
ENV JAVA_HOME="/usr/lib/jvm/default-jvm"

RUN cd /tmp && \
    wget --header "Cookie: oraclelicense=accept-securebackup-cookie;" "http://download.oracle.com/otn-pub/java/jdk/9.0.4+11/c2514751926b4512b076cc82f959763f/jdk-9.0.4_linux-x64_bin.tar.gz"
RUN tar -xzf "/tmp/jdk-9.0.4_linux-x64_bin.tar.gz"
RUN mkdir -p "/usr/lib/jvm"
RUN mv "jdk-9.0.4" "/usr/lib/jvm/java-${JAVA_VERSION}-oracle" && \
    ln -s "/usr/lib/jvm/java-${JAVA_VERSION}-oracle" "$JAVA_HOME" && \
    ln -s "$JAVA_HOME/bin/"* "/usr/bin/"
    #rm -f "$JAVA_HOME/lib/src.zip" && \

CMD ["jshell"]