Working with standalone Promtail
--------------------------------

Grafana Loki may be running in a k8s cluster, but other "normal" servers can still send their logs.

In `repo/promtail` there is a config file `config.yaml` to start with.

1. Start by editing it and inserting the ip to one of your worker nodes.

2. Prepare by opening the logfile `test123.log` in an editor

3. Start promtail. For this example we will start it with docker
```bash
cd promtail

docker container run -it --rm --name promtail -v $(pwd):/app -w /app grafana/promtail:2.2.0 -config.file config.yaml
```
