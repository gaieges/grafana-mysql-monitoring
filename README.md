# Simple grafana monitoring of MySQL metrics

> This repo attempts to demonstrate and provide a usable mysql install on docker, with grafana monitoring captured by prometheus

# Getting started

## Pre-req's 

Before getting started, ensure that you have the following installed locally:

- Vagrant
- Virtualbox

## Starting site

Simply run the following in this directory:

```bash
vagrant up
```

# MySQL 

Simple install that can be accessed via:

```
Host: 192.168.33.10
Port: 3306
User: root
Pass: myRootPassword123
```

# MySQL Metrics

In order to provide this info in a fancy way, I've hooked in grafana and set it up with the percona dashboards to visualize the info.  You can access the info here:

[Grafana Percona dashboards](http://192.168.33.10/dashboard/db/mysql-overview-percona-app?from=now-15m&to=now)

```
Username: admin
Password: admin
```

# How it works

The way that this vagrant instance is set up is by installing docker on the vagrant instance, and then creating a few containers to do all the work.  In this setup we have the following:

1. `mysql` container: simple setup of a mysql instance
1. `prometheus` container: timeseries database storage for metrics storage
1. `grafana` container: graphing tool to visualize information from mysql / prometheus
1. `prom_mysql_exporter` container: tool to collect data from mysql and store in prometheus


# Design decision

This repo is consciously designed to have two separate aspects of the setup (docker + ansible within vagrant), for 2 reasons: the grafana docker image doesn't contain much by way of configuration of the dashboards/users, and, that it should not be used as a production service.  It should be broken down into its separate components based on your desired infrastructure.  This is just a demo to get you up and running quickly. 
