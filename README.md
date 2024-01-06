# helm-chart-minimum-example

https://helm.sh/docs/chart_template_guide/builtin_objects/

初期化:
```
helm create simple-app
```

Dockerビルド:

```
docker build . -t simple-app
minikube image loadminikube image load simple-app:latest
```

develデモ:

```
$ helm install ./simple-app --generate-name --values simple-app/devel-values.yml
NAME: simple-app-1704551432
LAST DEPLOYED: Sat Jan  6 23:30:33 2024
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None

$ kubectl get pods
NAME                                     READY   STATUS      RESTARTS   AGE
simple-app-deployment-676fdf5c75-4l96m   0/1     Completed   0          2s
simple-app-deployment-676fdf5c75-7srrf   0/1     Completed   0          2s

$ kubectl logs simple-app-deployment-676fdf5c75-4l96m
simple-app-1704551432, default
simple-app, 0.1.0
開発用設定
```

prodデモ:

```
$ helm install ./simple-app --generate-name --values simple-app/prod-values.yml 
NAME: simple-app-1704551521
LAST DEPLOYED: Sat Jan  6 23:32:01 2024
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None

$ kubectl get pods
NAME                                   READY   STATUS      RESTARTS     AGE
simple-app-deployment-5b77bc47-cmzqf   0/1     Completed   1 (6s ago)   6s
simple-app-deployment-5b77bc47-tvltx   0/1     Completed   1 (6s ago)   6s

$ kubectl logs simple-app-deployment-5b77bc47-cmzqf
simple-app-1704551521, default
simple-app, 0.1.0
本番設定
```
