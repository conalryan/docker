FROM centos

RUN yum -y update \
	&& yum -y install tar unzip curl java-1.8.0-openjdk \
	&& yum clean all
ENV JAVA_HOME /usr/lib/jvm/jre

# Set Environment
ENV JBOSS_HOME /opt/jboss
ENV JBOSS_DEPLOY_DIR $JBOSS_HOME/standalone/deployments

# Add JBoss
ADD jboss/jboss-eap-7.2.0.zip /tmp

RUN unzip /tmp/jboss-eap-7.2.0.zip -d /tmp \
    && mkdir ${JBOSS_HOME} \
    && mv /tmp/jboss-eap-7.2/* ${JBOSS_HOME} \
    && chmod -R 755 ${JBOSS_HOME}

# Add war
# ADD ROOT.war ${JBOSS_DEPLOY_DIR}/

# Open Ports
EXPOSE 9999 9990 8080 4447

# Start JBoss
ENTRYPOINT ["/bin/bash", "-c", "$JBOSS_HOME/bin/standalone.sh"]
