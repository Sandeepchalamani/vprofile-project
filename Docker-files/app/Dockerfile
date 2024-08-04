FROM openjdk:11 AS BUILD_IMG
RUN apt  update && apt install maven -y
RUN git clone https://github.com/SandeepChal/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jrell
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
LABEL "Author"="Sandeep"

EXPOSE 8080
CMD ["catalina.sh","run"]
