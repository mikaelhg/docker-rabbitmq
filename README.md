### Learning Docker http://docker.io/ by creating a RabbitMQ container.

http://docs.docker.io/en/latest/use/builder/#dockerfile-examples

http://www.rabbitmq.com/install-debian.html

### To build:

    sudo docker build github.com/mikaelhg/docker-rabbitmq.git

### To run:

    sudo docker pull mikaelhg/docker-rabbitmq
    sudo docker run -p :5672 -p :15672 mikaelhg/docker-rabbitmq
    
### To persist your data:

Here we persistently save our data to the host machine's ``/tmp/rabbitmq/mnesia`` directory.

    mkdir -p /tmp/rabbitmq/mnesia
    chmod 777 /tmp/rabbitmq/mnesia
    sudo docker run -h rabbithost -p :5672 -p :15672 -v /tmp/rabbitmq/mnesia:/var/lib/rabbitmq/mnesia mikaelhg/docker-rabbitmq

Since RabbitMQ uses the ``$HOSTNAME`` in its data path, we need to explicitly set it for the container.

    $ sudo docker run -h rabbithost -p :5672 -p :15672 -v /tmp/rabbitmq/mnesia:/var/lib/rabbitmq/mnesia mikaelhg/docker-rabbitmq
    WARNING: Docker detected local DNS server on resolv.conf. Using default external servers: [8.8.8.8 8.8.4.4]
    
                  RabbitMQ 3.1.5. Copyright (C) 2007-2013 GoPivotal, Inc.
      ##  ##      Licensed under the MPL.  See http://www.rabbitmq.com/
      ##  ##
      ##########  Logs: /var/log/rabbitmq/rabbit@rabbithost.log
      ######  ##        /var/log/rabbitmq/rabbit@rabbithost-sasl.log
      ##########
                  Starting broker... completed with 6 plugins.

### To run in Vagrant VM:

1. Install virtualbox from https://www.virtualbox.org/ (or use your package manager)

2. Install vagrant from http://www.vagrantup.com/ (or use your package manager)

3. Clone this project with git

4. Run : ``vagrant up``

5. Open RabbitMQ Management Console from your browser: http://192.168.33.10:49153/
