# Trustworthy AI: algorithm assessment BB – CARiSMA

CARiSMA is a comprehensive open source software suite that enables system designers and security experts to perform automated compliance analyses, risk analyses and security analyses of software and system models. This allows users to consider security requirements early in the development process. Unified Modelling Language (UML) models are annotated with security-specific requirements that can be tailored to the users’ needs to cover a wide range of topics. Checks are performed on UML models, analyzing the models against the specified requirements and providing the user with detailed feedback on the models' compliance with the previously defined requirements.

## Design Document
See the design document [here](docs/).

## Building instructions

Checkout this repository and its submodules with:

```bash
git clone git@github.com:Prometheus-X-association/t-ai-carisma.git
git submodule init
git submodule update
```

Due to https://github.com/Prometheus-X-association/dataspace-connector/issues/38 the following is necessary to successfully build the dataspace connector:

```bash
echo "\n.git" >> dataspace-connector/.dockerignore
```

Then build the three containers (carisma + dataspace-connector + mongodb) with:

```bash
docker compose build
```

## Running instructions

Copy (and maybe adjust) the example env file for the dataspace connector and build the containers:

```bash
cp ./dataspace-connector/.env.sample ./.env
mkdir .data/
cp <your-authorized_keys> ./data/authorized_keys
docker compose up
```

To launch CARiSMA in the container on the docker host and use the GUI on your local host, connect to the carisma container from your local host via SSH (by default the container's SSH daemon is mapped to port 2222 of the docker host) with X11 forwarding enabled:

```bash
ssh -X -p 2222 root@<docker-host> /opt/carisma/carisma-launcher
```

Since the GUI is sent over network, performance depends on the connection quality between docker host and local host.

TODO: dataspace connector crashes.

## Example usage (TBD)
_Describe how to check some basic functionality of the BB._
E.g.:

Send the following requests to the designated endpoints:
| Endpoint      | Example input | Expected output   |
| ------------- | ------------- | ----------------- |
| /hello        | World         | 200, Hello World! |
|               |               |                   |
|               |               |                   |

## Unit testing
### Setup test environment
### Run tests
### Expected results

## Component-level testing
### Setup test environment
### Run tests
### Expected results
