FROM maven:3.9.9-eclipse-temurin-21-jammy as BUILD_IMAGE
LABEL "Project"="vprofile"
LABEL "Author"="Roberto"
RUN apt-get update && \
apt-get install -y git && \
git clone -b containers https://github.com/Roberto-1998/vprofile-project.git
WORKDIR /vprofile-project
RUN mvn install


FROM tomcat:10-jdk21
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE /vprofile-project/target/*.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]