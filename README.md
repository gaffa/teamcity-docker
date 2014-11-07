teamcity-docker
===============

docker containers for teamcity ci


Build Server
    docker build -t server src/main/docker/server/
Launch Server
    docker run -dt -p 8111:8111 --name server server

Build Agent
    docker build -t agent src/main/docker/agent/
Launch Agent
    Same Host:
        docker run -e TEAMCITY_SERVER=http://server:8111 --link server:server -dt --name agent agent
    Different Hosts:
        docker run -e TEAMCITY_SERVER=http://ip:8111 -dt -p 9090:9090 --name agent agent


You need to authorize the agent in the server. Also you may need to docker stop agent / docker start agent for agent upgrade.
