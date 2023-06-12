FROM openjdk:11 AS BUILD_IMG
RUN apt update && apt install maven -y
RUN git clone https://github.com/rahulrambo9/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install


FROM tomcat:9-jre11
LABEL "Project"="vprofile"
LABEL "Author"="Rahul"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMG vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]