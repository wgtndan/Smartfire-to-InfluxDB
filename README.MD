# Smartfire-to-InfluxDB

An example configuration that provides a Docker-Compose environment that can scrape metrics from the Smartfire's JSON endpoint, and pushes them to InfluxDB using Telegraf and the HTTP Input Plugin, this can then visualised in a Grafana dashboard as per the sample provided.

I wouldn't use this as it stands, but rather take what you need and adapt this to an existing environment.

## Prerequisites
- Docker
- Docker-Compose
- Smartfire v5 on Test Pilot Firmware (TBC)
- Experience with Docker and Docker-Compose
- Knowledge to identify your Smartfire's IP Address


## Configuration
Alter telegraf/config/telegraf.conf by replacing `smartfire.lan` on line 13 with the IP or Hostname of your Smartfire device.

## Usage

`docker-compose up -d`


## Detailed SmartFire Information
Everything here is fo reference to assist with understanding the data being accessed and what it means.

### Accessing native metrics from SF
Current state of the SF can be retrieved in JSON format at the following url:

`http://<Local-Smartfire-IP-Address>/rpc/SF.Status`

### Field Names
The following fields are contained within that JSON response:

| Variable | Description | Example Value |
| ----------- | ----------- | ----------- |
 | f1 | Wired Food Probe 1 Temperature | 61.3 |
 | f1t | Wired Food Probe 1 Target | 194 |
 | f2 | Wired Food Probe 2 Temperature | 0 |
 | f2t | Wired Food Probe 2 Target | 194 |
 | f3 | Wired Food Probe 3 Temperature | 0 |
 | f3t | Wired Food Probe 3 Target | 194 |
 | w1 | Wireless Food Probe 1 Temperature | 0 |
 | w1a | . | 0 |
 | w1t | Wireless Food Probe 1 Target | 160 |
 | w1r | . | 0 |
 | w1b | . | 0 |
 | w1s | . | 99 |
 | w2 | Wireless Food Probe 2 Temperature | 0 |
 | w2a | . | 0 |
 | w2t | Wireless Food Probe 2 Target | 110 |
 | w2r | . | 0 |
 | w2b | . | 0 |
 | w2s | . | 99 |
 | pit | Pit Probe Temperature | 0 |
 | pt | Pit Probe Target | 125 |
 | ph | Pit Probe High Alarm | 152 |
 | pl | Pit Probe Low Alarm | 100 |
 | sp | . | 112 |
 | fan | Fan power percentage | 100 |
 | mode | Operating Mode | 12 |
 | rssi | Wireless Signal Strength (RSSI) | -17 |
 | t | Current timestamp (epoch) | 1634413400 |
 | alarm | Is alarm firing? | 0 / 1 |
 | wifi | Is connected to Wifi? | 0 / 1 |
 | cloud | Is connected to Cloud? | 0 / 1 |