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
kubectl port-forward deployment/nginx-deployment 8080:8080 #KO
kubectl port-forward service/my-nginx 8080:80 #KO
kubectl port-forward service/my-nginx 8080:8080
```

Pour tester :
- [Tester](http://localhost:8080/) 

Sources :
- [Port forward](https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster/)

- [Différence entre service et deployment](https://matthewpalmer.net/kubernetes-app-developer/articles/service-kubernetes-example-tutorial.html)

### Suppression
```
kubectl delete deployment nginx-deployment
kubectl delete service my-nginx
```
* ou

```
kubectl delete -f 1-nginx-local.yaml
```

## Exercice 2

### Déploiement local Image Docker Custom
```
kubectl apply -f 2-custom-image.yaml 
kubectl port-forward deployment/myapp-deployment 8080:80
kubectl port-forward service/service-myapp 80:8080
kubectl delete deployment nginx-deployment
kubectl delete service my-nginx
```
## Exercice 3

### Déploiement local Whoami avec un ingress

**Activation des addons ingress minikube**
```
minikube addons enable ingress
minikube addons enable ingress-dns
```

**Lancement déploiement, service et ingress**
```
kubectl apply -f 3-nginx-ingress.yaml
```

**Liste des ingress créés**
*Il faut attendre quelques minutes qu'une adresse IP soit allouée à l'ingress*
```
kubectl get ingress
```

**Lancement tunnel minikube pour accéder à l'ingress**
```
minikube tunnel
```

**Test accès à l'app via l'ingress**
```
curl http://kubernetes.docker.internal
```

**Suppression**
```
kubectl delete -f 3-nginx-ingress.yaml
```

Sources :
- [Exemple 1](https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/)
- [Exemple 2](https://learn.microsoft.com/fr-fr/visualstudio/bridge/bridge-to-kubernetes-sample)

## Exercice 4

### Déploiement GKE Hello World
```
gcloud config set project <votreprojectid>
kubectl apply -f 4-gke-hello-world.yaml
kubectl get pod
kubectl get service
kubectl get deployment
```

**Liste des ingress créés**
*Il faut attendre quelques minutes qu'une adresse IP soit allouée à l'ingress + pour que l'appli soit accessible*
```
kubectl get ingress
```

**Test accès à l'app via l'ingress**
```
curl http://<url de votre loadbalancer>
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
kubectl delete -f 5-gke-deployment.yml
kubectl delete -f 5-gke-ingress.yaml
kubectl delete -f 5-gke-service.yaml
```

## Exercice 6

### Déploiement GKE Image Docker Custom avec GitlabCI
* [Déploiement avec gitlab-ci](https://blog.searce.com/gitlab-ci-cd-to-deploy-applications-on-gke-using-shared-runner-47f8c42817ac)
