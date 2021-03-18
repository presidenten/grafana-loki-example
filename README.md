Grafana Loki setup example
==========================

Description
-----------
This repo contains a simple example that shows how to roll out Grafana and Grafana Loki for experimentation

---

Requirements
------------
- A Kubernetes cluster
- Helm3 cli installed. Instructions: https://helm.sh/docs/intro/install/

---

Installation
------------

### *Step 1*

Write down a secure password in a file called `my-secret`

### *Step 2*

Run this helm command to install or upgrade:
```bash
helm upgrade --install --create-namespace \
  -n monitoring monitoring . \
  --set secret.pass=$(cat my-secret)
```

### *Step 3*

Wait for everything to spin up and login to Grafana with account `admin` and your secret password at `http://worker-node-ip:30000`.

---

What next?
----------
### Getting started with Loki

Read more here: [./docs/exploring.md](./docs/exploring.md)

### Optional extra configuration

Read more here: [./docs/optional-config.md](./docs/optional-config.md)

### Uninstall

Read more here: [./docs/uninstall.md](./docs/uninstall.md)
