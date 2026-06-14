# Checkmk Prometheus Nodeexporter Dashboard
 Checkmk Node Exporter Grafana Dashboard for Prometheus data exported from Checkmk using InfluxDB 2

![Screenshot of the Grafana Dashboard](https://github.com/nebuchadnezzar-network/cmk-prom-nodeexporter/blob/main/cmk-nodeexporter-hosts.png)

## Introduction 
This Dashboard was created to better support an Grafana integration with Checkmk. We all know dashboards are hard in Checkmk, but super easy in Grafana. This is an first attempt to solve the gap and work as inspiration for others who might want to visualize metrics from Checkmk in Grafana.

### Requirements
For this to work you would need to have an enterprise version of Checkmk (At least Pro) to leverage the InfluxDB integration. You would also need a Time Series database and be familiar with things like Prometheus. 

### Our workflow 
This is just an example workflow that shows how we produce and consume metrics in Grafana. 

1.) Data is exported using the InfluxDB connector 

2.) Data is forwared towards Nginx, this is to supply the Checkmk needed /ping endpoint that VM does not support

3.) Data is sent to a Victoria Metrics cluster (That supports Influx DB 2 format) 

4.) A normal Prometheus datasource is added to Grafana to explore, use drilldown and create dashboards 

### Usage
We already have workflows in Grafana and we already exports metrics into Victoria Metrics TSDB. This example dashboard uses some labels as variables. These are custom labels but shows how powerful it can be to use labels you set on, for example folders in Checkmk. In my view this is much more powerful compared to things like Alloy + Prometheus. 

The Dashboard is also multi-host aware compared to the regular node exporter dashboard you can download from Grafana. This mimics the "Windows" and "Linux" dashboards in Checkmk. 

### Future 
There are many interesting dashboards that could be created using Checkmk metrics. I'm currently investigating if an Active Directory dashboard could be created.

#### Note on AI
This work was mainly done by AI due to the number of panels but the initial work was done by hand. The mapping of node exporter metrics with Checkmk is the hard work, the Dashboard contains over 16.000 lines of data and would have taken ages to do manually. 
