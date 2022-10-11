FROM bitnami/python:3.7
MAINTAINER Bill Shetti "billshetti@gmail.com"
ENV REDIS_HOST="localhost"
ENV REDIS_PORT="6379"
ENV REDIS_PASSWORD=""

# This is a fake password for security testing:
ENV AZURE_CACHE_FOR_REDIS_ACCESS_KEY="a4ab3025YOLO42T0t@ll^f@keP@55w0rd"

ENV TRACER_HOST="localhost"
ENV TRACER_PORT="6832"
ENV JAEGER_HOST_AGENT="localhost"
ENV JAEGER_HOST_PORT="6832"

# needed for redis-cli ; the server is not used
RUN install_packages redis-server

COPY ./requirements.txt /app/requirements.txt
RUN pip3 install -r requirements.txt

ADD . /app
COPY entrypoint/docker-entrypoint.sh /usr/local/bin/
RUN chmod 777 /usr/local/bin/docker-entrypoint.sh
RUN ln -s /usr/local/bin/docker-entrypoint.sh /app # backwards compat

EXPOSE 5000
ENTRYPOINT ["docker-entrypoint.sh"]
#CMD ["python3", "cart.py"]