# Base image
FROM rockylinux:9.3.20231119

# Install JDK 17
RUN yum install -y wget
RUN wget https://corretto.aws/downloads/resources/17.0.11.9.1/java-17-amazon-corretto-devel-17.0.11.9-1.x86_64.rpm
RUN yum remove -y wget
RUN yum localinstall -y java-17-amazon-corretto-devel-17.0.11.9-1.x86_64.rpm
RUN rm java-17-amazon-corretto-devel-17.0.11.9-1.x86_64.rpm

# Set JAVA_HOME
ENV JAVA_HOME=/usr/lib/jvm/java-17-amazone-correcto.x86_64

# Set PATH to include Java binaries
ENV PATH=$PATH:$JAVA_HOME/bin