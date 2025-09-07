## PODS

```
apiVersion: v1
kind: Pod
metadata:
  name: primeiro-pod
spec:
  containers:
    - image: nginx
      name: nginx
```

#### Criando um simples pod:
```
kubectl run nginx --image nginx -o yaml --dry-run=client
```

#### Fazendo replace de um pod:
```
kubectl replace -f pod.yaml --force --grace-period=0
```

#### Editando um pod:
```
kubectl edit pod primeiro-pod
```
#### ou:
```
kubectl get pod primeiro-pod -o yaml > pod.yaml
```

#### Multiple containers:
```
apiVersion: v1
kind: Pod
metadata:
  name: primeiro-pod
spec:
  containers:
  - image: nginx
    name: nginx
    ports:
    - containerPort: 80
  - image: redis
    name: redis
    ports:
    - containerPort: 6379
```

