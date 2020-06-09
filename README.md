# DEPRECATED [![No Maintenance Intended](http://unmaintained.tech/badge.svg)](http://unmaintained.tech/)

This repository is now deprecated and it will be available until 01.06.2021.

StatsD + Graphite + Grafana
---------------------------

This image contains a sensible default configuration of StatsD, Graphite and Grafana


### Building the image ###

All you need as a prerequisite is having Docker installed on your machine. The container exposes the following ports:

- `80`: the Grafana web interface.
- `8125`: the StatsD port.
- `8126`: the StatsD administrative port.
- `2003`: the Graphite port.

The Dockerfile and supporting configuration files are available in our [Github repository](https://github.com/olx-inc/docker-graphite).
This comes specially handy if you want to change any of the StatsD, Graphite or Grafana settings, or simply if you want
to know how tha image was built. The repo also has `build` and `start` scripts to make your workflow more pleasant.

To build the container image from the repository you just need to run the following command:

```bash
$ docker build -t olx-inc/graphite https://github.com/olx-inc/docker-graphite.git
```

If you need to change some config files you just need to run the following command:

```bash
$ git clone https://github.com/olx-inc/docker-graphite.git
$ cd docker-graphite.git
$ <do some change>
$ docker build -t olx-inc/graphite .
```

To start a container with this image you just need to run the following command:

```bash
$ docker run -d -p 80:80 -p 8125:8125/udp -p 8126:8126 -p 2003:2003/udp --name graphite olx-inc/graphite
```

If you already have services running on your host that are using any of these ports, you may wish to map the container
ports to whatever you want by changing left side number in the `-p` parameters. Find more details about mapping ports
in the [Docker documentation](http://docs.docker.io/use/port_redirection/#port-redirection).


### Using the Dashboard ###

Once your container is running all you need to do is open your browser pointing to the host/port you just published and
play with the dashboard at your wish. We hope that you have a lot of fun with this image and that it serves it's
purpose of making your life easier. This should give you an idea of how the dashboard looks like when receiving data
from one of our toy applications:
