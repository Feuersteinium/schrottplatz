FROM eclipse-temurin:20-jdk-alpine

MAINTAINER Niklas Feuerstein, <contact@feuerstein.dev>



# Installing Java and Python and Wget
RUN echo http://dl-cdn.alpinelinux.org/alpine/edge/main >> /etc/apk/repositories && echo http://dl-cdn.alpinelinux.org/alpine/edge/testing >> /etc/apk/repositories && apk add --no-cache python3 wget py3-pip

ADD requirements.txt /home/container/requirements.txt
RUN pip install -r /home/container/requirements.txt --break-system-packages

# Adding Entrypoint
COPY ./entrypoint.sh /entrypoint.sh
RUN chmod 777 /entrypoint.sh


# Adding User
RUN adduser -D -h /home/container container
USER container
ENV  USER=container HOME=/home/container
WORKDIR /home/container


# Done!
CMD ["/bin/sh", "/entrypoint.sh"]
