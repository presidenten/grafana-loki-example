Grafana Loki setup example
==========================

tl;dr
-----
This repo contains a simple example that shows how to roll out Grafana and Grafana Loki for exeperimentation


Requirements
------------
- A Kubernetes cluster with nginx ingress and a domain name.
- Helm3 cli installed. Instructions: https://helm.sh/docs/intro/install/


Description
-----------
This helm chart contains a few nice defaults for Grafana, Loki, and Promtail.
It also rolls out an ingress rule for Grafana and a customizable secret with
credentials for the Grafana admin account,.


Installation
------------

*Step 1*

Write down a secure password in a file called `my-secret`

*Step 2*

Run this helm command to install or upgrade:
```bash
helm upgrade --install --create-namespace \
  -n monitoring monitoring . \
  --set secret.pass=$(cat my-secret)
```

*Step 3*

Wait for everything to spin up and login to Grafana with account `admin` and your secret password at `http://worker-node-ip:30000`.


Optional extra configuration
----------------------------
Checkout the official Grafana helm charts for configuration possibilities
- Grafana: https://github.com/grafana/helm-charts/blob/main/charts/grafana/values.yaml
- Loki: https://github.com/grafana/helm-charts/blob/main/charts/loki/values.yaml
- Promtail: https://github.com/grafana/helm-charts/blob/main/charts/promtail/values.yaml

A few extra goodies are available in `extra-goodies.yaml`.
To include them, use this command for installation or upgrade.

```bash
helm upgrade --install --create-namespace \
  -n monitoring monitoring . \
  --set secret.pass=$(cat my-secret) \
  -f extra-goodies.yaml
```

### Persistent storage
Uncomment the persistent storage sections in `values.yaml` and insert your storage class to get persistance.

### Connection to Ranchers cluster monitoring
Uncomment the prometheus datasource for Grafana in `values.yaml`


Uninstall
---------
To uninstall:
```bash
helm -n monitoring uninstall monitoring
```
