# Prometheus Speedtest Exporter

A Helm chart to deploy [MiguelNdeCarvalho/speedtest-exporter](https://github.com/MiguelNdeCarvalho/speedtest-exporter)

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
helm show values flouret/prometheus-speedtest-exporter > values.yaml
```

### Update the config

Edit `values.yaml` as required. Recommended values to set:

- Env var: `SPEEDTEST_CACHE_FOR`: duration in seconds to cache the results.
- Env var: `SPEEDTEST_SERVER`: server to use.
- Service annotations for prometheus scrape.

Example:
```yaml
service:
  annotations:
    prometheus.io/scrape-slow: "true"
    prometheus.io/port: "9798"

extraEnv:
  - name: SPEEDTEST_SERVER
    value: "3049"
  - name: SPEEDTEST_CACHE_FOR
    value: "1800" # Run a new test ever 30 minutes
```

## Install the chart

Run the following command to install the chart. Make sure to install to the correct namespace.

```shell
helm upgrade --install \
    --namespace prometheus \
    --values values.yaml
    prometheus-speedtest-exporter \
    flouret/prometheus-speedtest-exporter
```
