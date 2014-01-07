### Learning Docker http://docker.io/ by creating a RabbitMQ container.

http://docs.docker.io/en/latest/use/builder/#dockerfile-examples

http://www.rabbitmq.com/install-debian.html

### To build:

    sudo docker build github.com/mikaelhg/docker-rabbitmq.git

### To run:

    sudo docker pull mikaelhg/rabbitmq
    sudo docker run -p :5672 -p :15672 mikaelhg/rabbitmq
    
### To persist your data:

Here we persistently save our data to the host machine's ``/tmp/rabbitmq/mnesia`` directory.

    mkdir -p /tmp/rabbitmq/mnesia
    chmod 777 /tmp/rabbitmq/mnesia
    sudo docker run -h rabbithost -p :5672 -p :15672 -v /tmp/rabbitmq/mnesia:/var/lib/rabbitmq/mnesia mikaelhg/rabbitmq

Since RabbitMQ uses the ``$HOSTNAME`` in its data path, we need to explicitly set it for the container.

    $ sudo docker run -h rabbithost -p :5672 -p :15672 -v /tmp/rabbitmq/mnesia:/var/lib/rabbitmq/mnesia mikaelhg/rabbitmq
    WARNING: Docker detected local DNS server on resolv.conf. Using default external servers: [8.8.8.8 8.8.4.4]
    
                  RabbitMQ 3.1.5. Copyright (C) 2007-2013 GoPivotal, Inc.
      ##  ##      Licensed under the MPL.  See http://www.rabbitmq.com/
      ##  ##
      ##########  Logs: /var/log/rabbitmq/rabbit@rabbithost.log
      ######  ##        /var/log/rabbitmq/rabbit@rabbithost-sasl.log
      ##########
                  Starting broker... completed with 6 plugins.
