FROM java:8
MAINTAINER asideas

ENV TEAMCITY_PACKAGE TeamCity-8.1.4.tar.gz
ENV TEAMCITY_DOWNLOAD http://download.jetbrains.com/teamcity/
RUN wget -qO- $TEAMCITY_DOWNLOAD/$TEAMCITY_PACKAGE | tar xz -C /opt

EXPOSE 8111
CMD ["/opt/TeamCity/bin/teamcity-server.sh", "run"]