# Installation of monitoring for Longhorn

Pre-requisites
1. K8S cluster with Rancher monitoring installed (K8S v1.23.16)
2. Longhorn installed (v1.3.3)

## Deploy Longhorn Service Monitor

```
kubectl create -f service-monitor.yaml
```

After this you should see this Prometheus target:
* longhorn-system/longhorn-prometheus-servicemonitor

## Deploy Grafana dashboard

1. Log in to Grafana (username/password is in the rancher-monitoring-grafana secret).
2. From the Grafana menu choose Dashboards, then Import.
3. Paste the dashboard ID and load it. Specify to use the Prometheus datasource.

The dashboard can be found [here](https://grafana.com/grafana/dashboards/13032-longhorn-example-v1-1-0/) and it's ID copied from that page.

Once done, you should see a dashboard named something like *Longhorn v1.1.0*. 

## Deploy alerts

```
kubectl create -f alerts.yaml
```

This is based on [this](https://longhorn.io/docs/1.6.1/monitoring/alert-rules-example/).
Only the namespace was changed.

