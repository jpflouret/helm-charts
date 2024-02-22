# Prometheus Speedtest Exporter

A Helm chart to deploy [HON95/prometheus-nut-exporter](https://github.com/HON95/prometheus-nut-exporter)

## Requirements

- Helm 3

## Add the repo to Helm
```shell
helm repo add flouret https://charts.flouret.io/
helm repo update
```

## Configuration

### Generate a default configuration

Run this command to generate values.yaml:

```shell
helm show values flouret/prometheus-nut-exporter > values.yaml
```

### Update the config

Edit `values.yaml` as required. Recommended values to set:

\- Service annotations for prometheus scrape.

Example:
```yaml
service:
  annotations:
    prometheus.io/scrape-slow: "true"
    prometheus.io/port: "9798"

extraEnv:
  - name: TZ
    value: Americs/Vancouver
```

## Install the chart

Run the following command to install the chart. Make sure to install to the correct namespace.

```shell
helm upgrade --install \
    --namespace prometheus \
    --values values.yaml
    prometheus-nut-exporter \
    flouret/prometheus-nut-exporter
```
