# helm-chart-minimum-example

ビルドからデプロイまで:

```
docker build . -t simple-app
minikube image loadminikube image load simple-app:latest
```

デモ:
```
$ helm install ./simple-app --generate-name
NAME: simple-app-1704471669
LAST DEPLOYED: Sat Jan  6 01:21:09 2024
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None

$ kubectl get pods
NAME                                     READY   STATUS      RESTARTS      AGE
simple-app-deployment-678bcdc8bf-7kjpn   0/1     Completed   2 (27s ago)   29s
simple-app-deployment-678bcdc8bf-fp8bp   0/1     Completed   2 (27s ago)   29s

$ kubectl logs simple-app-deployment-678bcdc8bf-7kjpn 
Hello World
```
