# Multi-container

Check the behavior of the case one container in a multi-container pod fails

## apply

```
kubectl apply -f .
```

## port forward

```
kubectl port-forward svc/nginx -n naka 8080:80
```

## Availability of healthy container

open browser

You can see nginx home page

http://localhost:8080

## Conclusion

Failed container has no impact on the healthy container. (Readiness/Liveness failure nor OOMKilled)

You can intentionally check OOM case by the following change:

```diff
-        args: ["--vm", "1", "--vm-bytes", "14M", "--vm-hang", "1"]
+        args: ["--vm", "1", "--vm-bytes", "15M", "--vm-hang", "1"]
```
