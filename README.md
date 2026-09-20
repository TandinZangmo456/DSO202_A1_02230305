## Appendix: raw evidence
]633;E;for f in evidence/*.txt;dc61bbac-891e-4a75-982d-03f7c9dbe77e]633;C### evidence/7a-1-create.txt
```
{"id":4,"title":"Assignment demo task","description":"created via curl","status":"pending","created_at":"2026-09-20T13:41:00.678Z"}
```

### evidence/7a-2-list.txt
```
[{"id":1,"title":"Set up kind cluster","description":"Bring up the local cluster from Practical 1","status":"done","created_at":"2026-09-20T03:22:44.560Z"},{"id":2,"title":"Write namespace manifest","description":"One namespace for all assignment resources","status":"in_progress","created_at":"2026-09-20T03:22:44.560Z"},{"id":3,"title":"Wire ConfigMap and Secret","description":"DB_* and POSTGRES_* must carry matching values","status":"pending","created_at":"2026-09-20T03:22:44.560Z"},{"id":4,"title":"Assignment demo task","description":"created via curl","status":"pending","created_at":"2026-09-20T13:41:00.678Z"}]
```

### evidence/7a-3-update.txt
```
{"id":4,"title":"Assignment demo task","description":"updated via curl","status":"done","created_at":"2026-09-20T13:41:00.678Z"}
```

### evidence/7a-4-get-one.txt
```
{"id":4,"title":"Assignment demo task","description":"updated via curl","status":"done","created_at":"2026-09-20T13:41:00.678Z"}
```

### evidence/7a-5-delete.txt
```
HTTP/1.1 204 No Content
X-Powered-By: Express
Access-Control-Allow-Origin: *
Date: Sun, 20 Sep 2026 13:41:08 GMT
Connection: keep-alive
Keep-Alive: timeout=5


```

### evidence/7a-6-after-delete.txt
```
HTTP/1.1 404 Not Found

```

### evidence/7b-dns.txt
```
{"status":"ok","db":"connected"}Server:		10.96.0.10
Address:	10.96.0.10:53

** server can't find backend-svc.cluster.local: NXDOMAIN

** server can't find backend-svc.cluster.local: NXDOMAIN

Name:	backend-svc.dso202-assignment-01.svc.cluster.local
Address: 10.96.46.24

** server can't find backend-svc.svc.cluster.local: NXDOMAIN

** server can't find backend-svc.svc.cluster.local: NXDOMAIN



```

### evidence/7c-1-create-before.txt
```
{"id":5,"title":"Survives pod deletion","description":"created before deleting the backend Pod","status":"pending","created_at":"2026-09-20T13:46:32.696Z"}
```

### evidence/7c-2-pods-before.txt
```
NAME                        READY   STATUS    RESTARTS   AGE   IP            NODE                   NOMINATED NODE   READINESS GATES
backend-59d57b4c77-drd7h    1/1     Running   0          10h   10.244.0.8    dso202-control-plane   <none>           <none>
db-67977cdc6c-qjxgt         1/1     Running   0          10h   10.244.0.7    dso202-control-plane   <none>           <none>
frontend-5bbc4ff6df-t754b   1/1     Running   0          17m   10.244.0.11   dso202-control-plane   <none>           <none>

```

### evidence/7c-3-delete.txt
```
pod "backend-59d57b4c77-drd7h" deleted from dso202-assignment-01 namespace

```

### evidence/7c-4-pods-after.txt
```
NAME                        READY   STATUS    RESTARTS   AGE   IP            NODE                   NOMINATED NODE   READINESS GATES
backend-59d57b4c77-x7nvf    1/1     Running   0          56s   10.244.0.12   dso202-control-plane   <none>           <none>
db-67977cdc6c-qjxgt         1/1     Running   0          10h   10.244.0.7    dso202-control-plane   <none>           <none>
frontend-5bbc4ff6df-t754b   1/1     Running   0          18m   10.244.0.11   dso202-control-plane   <none>           <none>

```

### evidence/7c-5-tasks-after-backend-delete.txt
```
[{"id":1,"title":"Set up kind cluster","description":"Bring up the local cluster from Practical 1","status":"done","created_at":"2026-09-20T03:22:44.560Z"},{"id":2,"title":"Write namespace manifest","description":"One namespace for all assignment resources","status":"in_progress","created_at":"2026-09-20T03:22:44.560Z"},{"id":3,"title":"Wire ConfigMap and Secret","description":"DB_* and POSTGRES_* must carry matching values","status":"pending","created_at":"2026-09-20T03:22:44.560Z"},{"id":5,"title":"Survives pod deletion","description":"created before deleting the backend Pod","status":"pending","created_at":"2026-09-20T13:46:32.696Z"}]
```

### evidence/7c-6-delete-db.txt
```
pod "db-67977cdc6c-qjxgt" deleted from dso202-assignment-01 namespace

```

### evidence/7c-7-pvc.txt
```
NAME     STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
db-pvc   Bound    pvc-c123cdf6-24cf-4730-9ae6-d1dff0e3f648   1Gi        RWO            standard       <unset>                 10h

```

### evidence/7c-8-tasks-after-db-delete.txt
```
[{"id":1,"title":"Set up kind cluster","description":"Bring up the local cluster from Practical 1","status":"done","created_at":"2026-09-20T03:22:44.560Z"},{"id":2,"title":"Write namespace manifest","description":"One namespace for all assignment resources","status":"in_progress","created_at":"2026-09-20T03:22:44.560Z"},{"id":3,"title":"Wire ConfigMap and Secret","description":"DB_* and POSTGRES_* must carry matching values","status":"pending","created_at":"2026-09-20T03:22:44.560Z"},{"id":5,"title":"Survives pod deletion","description":"created before deleting the backend Pod","status":"pending","created_at":"2026-09-20T13:46:32.696Z"}]
```

### evidence/7c-9-replicasets.txt
```
NAME                  DESIRED   CURRENT   READY   AGE
backend-59d57b4c77    1         1         1       11h
db-67977cdc6c         1         1         1       11h
frontend-5bbc4ff6df   1         1         1       65m

```

### evidence/7c-backend-watch.txt
```
NAME                        READY   STATUS    RESTARTS   AGE
backend-59d57b4c77-drd7h    1/1     Running   0          10h
db-67977cdc6c-qjxgt         1/1     Running   0          10h
frontend-5bbc4ff6df-t754b   1/1     Running   0          17m
backend-59d57b4c77-drd7h    1/1     Terminating   0          10h
backend-59d57b4c77-drd7h    1/1     Terminating   0          10h
backend-59d57b4c77-x7nvf    0/1     Pending       0          0s
backend-59d57b4c77-x7nvf    0/1     Pending       0          0s
backend-59d57b4c77-x7nvf    0/1     ContainerCreating   0          1s
backend-59d57b4c77-x7nvf    0/1     ContainerCreating   0          1s
backend-59d57b4c77-x7nvf    1/1     Running             0          1s
backend-59d57b4c77-drd7h    0/1     Error               0          10h
backend-59d57b4c77-drd7h    0/1     Error               0          10h
backend-59d57b4c77-drd7h    0/1     Error               0          10h
backend-59d57b4c77-drd7h    0/1     Error               0          10h

```

### evidence/7d-1-declarative.txt
```
service/backend-svc unchanged

```

### evidence/7d-2-imperative.txt
```
service/backend-svc-imperative exposed

```

### evidence/7d-3-both-services.txt
```
NAME                     TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE   LABELS
backend-svc              ClusterIP   10.96.46.24     <none>        8080/TCP         11h   app.kubernetes.io/name=backend,app.kubernetes.io/part-of=task-tracker,tier=backend
backend-svc-imperative   ClusterIP   10.96.190.101   <none>        8080/TCP         0s    app.kubernetes.io/name=backend,app.kubernetes.io/part-of=task-tracker,tier=backend
db-svc                   ClusterIP   None            <none>        5432/TCP         11h   app.kubernetes.io/name=db,app.kubernetes.io/part-of=task-tracker,tier=database
frontend-svc             NodePort    10.96.67.228    <none>        8080:30080/TCP   10h   app.kubernetes.io/name=frontend,app.kubernetes.io/part-of=task-tracker,tier=frontend

```

### evidence/7d-4-diff.txt
```
4,7c4
<   annotations:
<     kubectl.kubernetes.io/last-applied-configuration: |
<       {"apiVersion":"v1","kind":"Service","metadata":{"annotations":{},"labels":{"app.kubernetes.io/name":"backend","app.kubernetes.io/part-of":"task-tracker","tier":"backend"},"name":"backend-svc","namespace":"dso202-assignment-01"},"spec":{"ports":[{"name":"http","port":8080,"targetPort":8080}],"selector":{"app.kubernetes.io/name":"backend","tier":"backend"},"type":"ClusterIP"}}
<   creationTimestamp: "2026-09-20T03:26:32Z"
---
>   creationTimestamp: "2026-09-20T14:30:36Z"
12c9
<   name: backend-svc
---
>   name: backend-svc-imperative
14,15c11,12
<   resourceVersion: "3753"
<   uid: 3a1cd28e-5e7f-4e35-b841-34ab56f40507
---
>   resourceVersion: "14449"
>   uid: 2d85676e-f0f1-4318-a27f-e50e281e19ab
17c14
<   clusterIP: 10.96.46.24
---
>   clusterIP: 10.96.190.101
19c16
<   - 10.96.46.24
---
>   - 10.96.190.101
25,26c22
<   - name: http
<     port: 8080
---
>   - port: 8080

```

