# mongo-db-Server-using-K8s
It is a Kubernetes project in which mongo-db server is created and accessed through mongo-db Express with persistent volume implemented using minikube .
```
minikube start --driver=hyperv #keep driver as per your case
kubectl apply -f secrets.yaml
kubectl apply -f config-map.yaml
minikube ssh "sudo mkdir -p /data/db && sudo chmod 777 /data/db" #create hostpath and  give proper permission .
kubectl apply -f persistent_volume.yaml
kubectl apply -f pvc.yaml
kubectl apply -f mongodb-deployement.yaml
kubectl apply -f mongo-express-deployement.yaml
```
Implement ingress and download ingress controller
```
minikube addons enable ingress
kubectl apply -f mongo-express-ingress
```
Add `myapp.com` to \etc\hosts with ip given to the ingress created . (do `kubectl get ingress`)
NOTE : In real production environment never upload your secrets on git repo their tools like Vault are used .
Learned basics of Kubernetes from [TechWorld with Nana](https://youtu.be/X48VuDVv0do?si=iccivrbcDnvOGzOy)
