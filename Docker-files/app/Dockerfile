FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/SubodhaDash/Devops_Projects.git
RUN cd Devops_Projects && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "PROJECT"="Vprofile"
LABEL "Author"="Subodha"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE Devops_Projects/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh", "run" ]
