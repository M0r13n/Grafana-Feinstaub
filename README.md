# Particulate matter sensor (luftdaten.info) Grafana Dashboard

This project provides Docker based monitoring for your [luftdaten.info](https://github.com/opendata-stuttgart/meta) particulate matter sensor.

## Requirements

- Docker & docker-compose
- a simple machine with `>=2gb` of memory (a simple Raspberry PI 3 will do the job)

## Installation

At first you need an up and running sensor. Please refer to  [luftdaten.info](https://github.com/opendata-stuttgart/meta) for building instructions. Make sure that your ESP8266 is reachable in your local network.

#### Setup Grafana and InfluxDB

- install Ubuntu server on your pi (or any other machine)
- install Docker & `docker-compose`
- ssh into your pi
- execute the following steps
```bash
# Clone this repo
git clone TBD

# Head into the repo
cd grafana-feinstaub

# Start the services (this may take a while)
docker-compose up -d
```

After that the following services are running:

1. Grafana
    - Accessible at `http://<YOUR_MACHINE_IP>:3000`
2. InfluxDB
    - Accessible at `http://<YOUR_MACHINE_IP>:8086`
    - By default a new database `sensorcommunity` is created that is also already available as a datasource in Grafana

#### Setup particulate sensor

1. Open the web page of your particulate sensor (e.g. `http://192.168.1.35`)
2. Open the `configuration` tab
3. Open the `API` tab
4. Check the checkbox `send data to InfluxDB` (uncheck HTTPS)
5. Change the server to match the IP of your PI.
6. Click `save and reboot`

Your sensor should now start sending data to your local InfluxDB (it still continues to send it's data to all other APIs).
 
## Usage

Log into Grafana with `admin`:`admin`. You will be prompted to change your password on first login.