# Application Chart & Manifest with Fluent Bit as a Log to Metrics Exporter

## Assumptions

1. This tutorial only applies to Linux nodes and assumes you’re familiar with Kubernetes & Helm charts
2. The application logs are assumed to be in JSON for simpler parsing.

## Fluent Bit Configuration

1. Parser: A parser is needed as we are trying to scrap logs from the node source file, the logs are not exactly in JSON. but with the help of a custom parser we can extract needed app JSON for further operations. Further Documentation.
2. Input: We are trying to get contents of the file/var/log/containers/<pod_name>_<namespace>_<container_name>*.log so for our case /var/log/containers/${HOSTNAME}_nginx-app*.log. Further Documentation.
3. Filters/metrics: The rules mentioned below are basic rules that can be used as basic building blocks for more complex rules depending on the use-case. Further Documentation.
4. Output: Using prometheus_exporter as a output to display metrics generated. Further Documentation.

## How to deploy

```
helm upgrade --install <app-name> charts/  -n <namespace>
```