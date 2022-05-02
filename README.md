## Run this command
```bash
#!/bin/bash

echo "Creating database"
kubectl create -f https://raw.githubusercontent.com/yasin-cs-ko-ak/kubernetes-django/master/kubernetes/database/replication-controller.yaml
sleep 10
kubectl create -f https://raw.githubusercontent.com/yasin-cs-ko-ak/kubernetes-django/master/kubernetes/database/service.yaml
sleep 10

echo "Creating django-pods"
kubectl create -f https://raw.githubusercontent.com/yasin-cs-ko-ak/kubernetes-django/master/kubernetes/app/replication-controller-app-django.yaml
sleep 10
kubectl create -f https://raw.githubusercontent.com/yasin-cs-ko-ak/kubernetes-django/master/kubernetes/app/service.yaml
sleep 10
kubectl get pod | grep django
echo "Run this command: kubectl exec <pod-name> -- python /app/manage.py migrate"
echo "Run this command: kubectl exec -it <pod-name> -- python /app/manage.py createsuperuser"
```
