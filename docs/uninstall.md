Uninstall
---------

## To uninstall

```bash
helm -n monitoring uninstall loki-stack
```

---

## If you installed the log-generator

```bash
kubectl delete deployment log-generator
```
