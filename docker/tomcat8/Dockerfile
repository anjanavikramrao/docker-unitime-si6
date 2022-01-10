FROM tomcat:8.0.50-jre8-slim

RUN apt-get update && \
	apt-get install -y wget unzip && \
	wget --no-check-certificate https://jdbc.postgresql.org/download/postgresql-42.3.1.jar && \
	echo 'JAVA_OPTS=”-Djava.awt.headless=true -Xmx2g -XX:+UseConcMarkSweepGC”' >> /etc/default/tomcat8 && \
	cp postgresql-42.3.1.jar /usr/local/tomcat/lib && \
	mkdir /usr/local/tomcat/data && \
	sed -i "s|-Djava.protocol.handler.pkgs=org.apache.catalina.webresources|-Djava.protocol.handler.pkgs=org.apache.catalina.webresources -Djava.awt.headless=true -Xmx2g -XX:+UseConcMarkSweepGC|g" /usr/local/tomcat/bin/catalina.sh && \
	echo 'tmtbl.custom.properties=/usr/local/tomcat/conf/unitime.properties' >> /usr/local/tomcat/conf/catalina.properties && \
	chmod 777 /usr/local/tomcat/data
	
COPY UniTime.war /usr/local/tomcat/webapps
COPY unitime.properties /usr/local/tomcat/conf/unitime.properties