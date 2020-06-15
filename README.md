Apply the yaml,

assuming a port forward of:

```
kubectl port-forward $(kubectl get pod --selector=eventlistener=github-listener-interceptor -oname) 8080
```

and invoke with:

```
curl -X POST \
  http://localhost:8080 \
  -H 'Content-Type: application/json' \
  -d '{
  "registry": {"url": "gcr.io/snichols-vmw/colorz:latest"},
  "repository": {"url": "https://github.com/spring-projects/spring-petclinic"}
}'
```

or on the custer:
```
curl -X POST \
  http://el-listener.default.svc.cluster.local:8080 \
  -H 'Content-Type: application/json' \
  -d '{
  "registry": {"url": "gcr.io/snichols-vmw/colorz:latest"},
  "repository": {"url": "https://github.com/spring-projects/spring-petclinic", "revision":"main"}
}'
```

b5711257affd51636b81ffb5b4693182ba37d54a

```
curl -X POST \
  http://el-listener.default.svc.cluster.local:8080 \
  -H 'Content-Type: application/json' \
  -d '{
  "registry": {"url": "gcr.io/snichols-vmw/colorz:latest"},
  "repository": {"url": "https://github.com/spring-projects/spring-petclinic", "revision":"7376625c3bf8f610d64def65293a093376d6c6dc"}
}'
```
