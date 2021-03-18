
Optional extra configuration
----------------------------
A few extra goodies are available in `extra-goodies.yaml`.

The goodies consist of:

- grafana sidecar that can load dashboards via config maps
- labels for grafana to help with monitoring grafana itself
- 29 day log retention in loki
- promtail tolerations that loads the client on all nodes


Use this command to install or upgrade, and apply the extra options.


```bash
helm upgrade --install --create-namespace \
  -n monitoring monitoring . \
  --set secret.pass=$(cat my-secret) \
  -f extra-goodies.yaml
```

---

## Enable Persistent storage

Uncomment the persistent storage sections in `values.yaml` and insert your storage class to get persistance.

---

## Connection to Ranchers cluster monitoring

Uncomment the prometheus datasource for Grafana in `values.yaml`

---

## Using Crio instead of Docker runtime?

Uncomment `- cri: {}` in `values.yaml` in the promtail section, and comment out `- docker: {}`

---

## More configurations

Checkout the official Grafana helm charts for configuration possibilities

- Grafana: https://github.com/grafana/helm-charts/blob/main/charts/grafana/values.yaml

- Loki: https://github.com/grafana/helm-charts/blob/main/charts/loki/values.yaml

- Promtail: https://github.com/grafana/helm-charts/blob/main/charts/promtail/values.yaml
