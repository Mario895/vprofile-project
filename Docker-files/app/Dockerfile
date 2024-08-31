FROM openjdk:11 AS BUILD_IMAGE
LABEL "Project"="Vprovile"
LABEL "Author"="Mario"
RUN apt update && apt install maven -y
RUN git clone https://github.com/Mario895/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprovile"
LABEL "Author"="Mario"
RUN rm -rf /usr/local/tomcat/webaps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]

