# Exercices K8S avec Kubernetes sur Docker Desktop

## Exercice 1

### Déploiement local Nginx  
```
kubectl apply -f 1-nginx-local.yaml 
kubectl get svc
kubectl get service
kubectl get services
kubectl get deployment
kubectl get deployments
kubectl describe deployment nginx-deployment
kubectl describe svc my-nginx
kubectl get po
kubectl get pod
kubectl get pods        
kubectl get replicaset
kubectl get all -o wide
kubectl port-forward deployment/nginx-deployment 8080:80
kubectl port-forward service/my-nginx 8080:80
kubectl port-forward service/my-nginx 8080:8080
```

Pour tester :
- [Tester](http://localhost:8080/) 
Sources :
- [Explication port forward](https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster/)

### Suppression
```kubectl delete deployment nginx-deployment
kubectl delete service my-nginx
```
* ou
```kubectl delete -f 1-nginx-local.yaml
```

## Exercice 2

### Déploiement local Image Docker Custom
```
kubectl apply -f 2-custom-image.yaml 
kubectl port-forward deployment/myapp-deployment 8080:80
kubectl delete deployment nginx-deployment
kubectl delete service my-nginx
```
## Exercice 3

### Déploiement local Whoami avec un ingress
```
kubectl apply -f 3-nginx-custom-not-ready.yaml
kubectl port-forward deployment/myapp-deployment 8080:80
kubectl delete deployment nginx-deployment
kubectl delete service my-nginx
```

## Exercice 4

### Déploiement GKE Hello World
```
gcloud config set project <votreprojectid>
kubectl apply -f 4-gke-hello-world.yaml
```

Sources :
* https://cloud.google.com/kubernetes-engine/docs/tutorials/http-balancer
* https://logz.io/blog/containerized-app-gke/

## Exercice 5

### Déploiement GKE Image Docker Custom
```
gcloud config set project <votreprojectid>
kubectl create secret docker-registry regsecret --docker-server=<your-registry-server> --docker-username=<your-name> --docker-password=<your-pword> --docker-email=<your-email>
kubectl apply -f 5-gke-deployment.yml
kubectl apply -f 5-gke-ingress.yaml
kubectl apply -f 5-gke-service.yaml
```

## Exercice 6

### Déploiement GKE Image Docker Custom avec GitlabCI
* [Déploiement avec gitlab-ci](https://blog.searce.com/gitlab-ci-cd-to-deploy-applications-on-gke-using-shared-runner-47f8c42817ac)
