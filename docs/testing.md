
Getting started with Loki
-------------------------

There is a log-generator that can be rolled out to get started in the experimentation:

```bash
kubectl create deployment log-generator --image=presidenten/log-generator
```

- When until its up and running, then log into Grafana as user `admin` and use your secret password that you put in the `my-secret` file.

- Enter the `explore` section

<img src="./assets/explore.png" width="600" />

- Enter a query the query to select log stream.
Working with the job label is a great way to filter streams.

- Try `{job="default/log-generator"}`

<img src="./assets/query.png" width="600" />

- Then run the query to see the logs, press the Live button instead to follow the logs in near realtime.

<img src="./assets/run.png" width="600" />

---

Exploring
---------

Read more on Grafanas pages on `LogQL`

https://grafana.com/docs/loki/latest/logql/
