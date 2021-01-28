FROM python:3.6

# Create app directory
RUN mkdir -p /home/backend
RUN apt-get update \
    && apt-get -y install nano
# Cleanup after apt-get commands
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    /var/cache/apt/archives/*.deb /var/cache/apt/*cache.bin
# Activate WORKING DIR
WORKDIR /home/backend
# Copying requirements
COPY requirements.txt /tmp/requirements.txt
# Install the app dependencies
# ToDo Refactor requirements
RUN pip install mysqlclient
RUN pip install -r /tmp/requirements.txt
# Envs

# ADD the source code and entry point into the container
ADD . /home/backend
#ADD entrypoint.sh /home/backend/app/entrypoint.sh
# Making entry point executable
#RUN chmod +x entrypoint.sh
# Exposing port
EXPOSE 8000
# Entry point and CMD
#ENTRYPOINT ["/home/backend/app/entrypoint.sh"]


