Uninstall
---------

To uninstall:
```bash
helm -n monitoring uninstall monitoring
```

If you installed the log-generator:
```bash
kubectl delete deployment log-generator
```
