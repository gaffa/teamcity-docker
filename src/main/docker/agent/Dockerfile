FROM ubuntu:14.10
MAINTAINER asideas

# java 8 repo
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv EEA14886
RUN echo 'deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main' | sudo tee /etc/apt/sources.list.d/webupd8.list
RUN echo debconf shared/accepted-oracle-license-v1-1 select true | sudo debconf-set-selections

# maven repo
RUN echo 'deb http://ppa.launchpad.net/natecarlson/maven3/ubuntu precise main' | sudo tee /etc/apt/sources.list.d/natec.list

# apt-get update
RUN apt-get --quiet update

# install java
RUN apt-get --quiet --yes install oracle-java8-installer
RUN apt-get --quiet --yes install oracle-java8-set-default

# install tools needed for build
RUN apt-get -y --force-yes install git libfontconfig maven3 gradle nodejs nodejs-legacy npm docker.io

# install node packages
RUN npm install -g karma karma-cli karma-phantomjs-launcher karma-jasmine karma-jasmine-jquery karma-junit-reporter karma-ng-html2js-preprocessor
RUN npm install karma karma-cli karma-phantomjs-launcher karma-jasmine karma-jasmine-jquery karma-junit-reporter karma-ng-html2js-preprocessor

# link maven-binary
RUN rm -f /usr/bin/mvn
RUN ln -s /usr/share/maven3/bin/mvn /usr/bin/mvn

# expose port
EXPOSE 9090

# install teamcity agent
ADD agent.sh /agent.sh
CMD sudo -s -- sh -c "TEAMCITY_SERVER=$TEAMCITY_SERVER bash /agent.sh run"