# Base image
FROM redhat/ubi8:8.5

RUN yum -y update

RUN yum -y install java-11-openjdk && \
    yum -y install vim unzip && \
    yum -y install net-tools

RUN yum install -y procps

ENV JBOSS_HOME /opt/wildfly

RUN useradd jboss

USER root

RUN cd /opt  && \
    mkdir wildfly && \ 
    chown -R jboss:jboss ${JBOSS_HOME} && \
    chmod -R g+rw ${JBOSS_HOME} 

# Create module postgres
#RUN mkdir -p /opt/wildfly/modules/system/layers/base/org/postgresql/main/

#RUN -rf /run/httpd/*
#RUN /usr/sbin/httpd


USER jboss
#CMD ["/usr/sbin/init"]
# Run
CMD ["/opt/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0", "-c", "standalone.xml", "--debug", "9797"]

#EXPOSE 80 8080 9990 8443
EXPOSE 8080 9990 8009 8443 9797