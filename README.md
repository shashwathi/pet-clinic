Apply the yaml,

assuming a port forward of:

```
kubectl port-forward $(kubectl get pod --selector=eventlistener=github-listener-interceptor -oname) 8080
```
invoke with:

```
curl -X POST \
  http://localhost:8080 \
  -H 'Content-Type: application/json' \
  -d '{
  "registry": {"url": "shashwathin/pet-clinic:latest"},
  "repository": {"url": "https://github.com/spring-projects/spring-petclinic", "revision":"main"}
}'
```


```
curl -X POST \
  http://localhost:8080 \
  -H 'Content-Type: application/json' \
  -d '{
  "registry": {"url": "shashwathin/pet-clinic:latest"},
  "repository": {"url": "https://github.com/spring-projects/spring-petclinic", "revision":"d367e2b4b41a2de899b0f438bc984a7c1c011b77"}
}'
```
