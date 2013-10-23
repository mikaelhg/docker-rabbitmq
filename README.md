### Learning Docker http://docker.io/ by creating a RabbitMQ container.

http://docs.docker.io/en/latest/use/builder.html#dockerfile-examples

http://www.rabbitmq.com/install-debian.html

### To build:

    sudo docker build https://github.com/mikaelhg/docker-rabbitmq.git

### To run:

    sudo docker pull mikaelhg/rabbitmq
    sudo docker run -p :5672 -p :15672 mikaelhg/rabbitmq
    
### To persist your data:

Here we persistently save our data to the host machine's ``/tmp/rabbitmq/mnesia`` directory.

    mkdir -p /tmp/rabbitmq/mnesia
    chmod 777 /tmp/rabbitmq/mnesia
    sudo docker run -p :5672 -p :15672 -v /tmp/rabbitmq/mnesia:/var/lib/rabbitmq/mnesia mikaelhg/rabbitmq
