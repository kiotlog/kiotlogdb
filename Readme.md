# Kiotlog Platform Microservices

## Running Kiotlog plaform

### Build microservices

Use provided `docker-compose.yml` to build Kiotlog microservices Docker images:

    $ docker-compose build

### Prepare Kiotlog services deployment

In order to run the Kiotlog platform, you need at least pre-configured instances for PostgreSQL (both for devices/sensors catalog and data points timeseries) and [EMQ](http://emqtt.io/) (for MQTT and MQTT-SN). The [Dockerfiles](https://bitbucket.org/kiotlog/dockerfiles) repository contains base configurations and Dockerfiles for building and deploying PostgreSQL with preloaded Kiotlog DB schema, EMQ with pre-configured MQTT-SN plugin, and other services (Grafana, Node-Red, InfluxDB).

#### Istructions

1.  Build Kiotlog microservices as per previous paragraphs.
2.  Change to upper directory and pull Kiotlog [Dockerfiles](https://bitbucket.org/kiotlog/dockerfiles).

        $ git pull https://bitbucket.org/kiotlog/dockerfiles

3. Follow istructions at [Dockerfiles/Readme.md](https://bitbucket.org/kiotlog/dockerfiles) to create the Kiotlog deploying environment. 

5.  Run Kiotlog platform

        $ docker-compose -f docker-compose.local.yml up -d
        $ docker-compose logs -f

6.  Platform will start receiving data from Kiotlog test devices via The Things Network.
7.  Connect to [Local Grafana](http://localhost:3000) and create your dashboard or import the demo dashboard provided at [Dockerfiles/grafana/Kiotlog Demo.json](https://bitbucket.org/kiotlog/dockerfiles/raw/73103702fcfe109312002d0b1a7f2a5a471f3b26/grafana/Kiotlog%20Demo.json).