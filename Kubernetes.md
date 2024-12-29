# Kubernetes
## minikube

```bash
# install minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64

# put this line in your ~/.bashrc
alias kubectl="minikube kubectl --"

# start the cluster
minikube start
minikube status
minikube stop
minikube delete
minikube dashboard
minikube ip
minikube ssh

```
## namespaces
```bash
# get the list of namespaces
kubectl get namespaces
kubectl create namespace ns1
kubectl delete namespace ns1

```

## nodes
```bash
# get the list of nodes
kubectl get nodes
kubectl describe node <nodename>
kubectl describe node minikube
kubectl delete node minikube
```

## pods
```bash
kubectl get pods
# create a pod using a yaml file (named pod1.yaml)
kubectl create -f pod1.yaml
kubectl describe pod pod1
kubectl delete pod pod1
```

## running custom application in kubernetes cluster 
```bash
docker image build -t website .
# tag the image with docker hub username
docker image tag website <username>/website
docker image tag website pythoncpp/website
# push the image to docker hub
docker image push <username>/website
docker image push pythoncpp/website
```

## replica sets
- used to create replicas of your pods
- similar to service in docker swarm - replica set manages the pods which are matching with the specified label
```bash
kubectl get replicasets
kubectl get rs
kubectl create -f replica-set.yaml
kubectl describe replicaset rs1
kubectl describe rs rs1
# delete a replica set
kubectl delete replicaset rs1
```

## deployment
- used to create replicas of your pod using replica set
- deployment creates a replica set behind the scene
- supports the rollout
  - which is responsible for upgrading or downgrading (rollback) the application version
- in industry, deployment is preferred over replica set
```bash
# get the list of deployments
kubectl get deployments
kubectl get deploy
kubectl describe deployment <name>
kubectl describe deployment deployment1
kubectl delete deployment <name>
kubectl delete deployment deployment1
```

## services
- acts as a load balancer
```bash
# get list of services
kubectl get services
kubectl get svc
kubectl describe service service1
kubectl delete service <name>
kubectl delete service service1
# restart the deployment
kubectl rollout restart deployment <deployment-name>
kubectl rollout restart deployment mywebsite

# undo the deployment
kubectl rollout undo deployment <deployment name>
kubectl rollout undo deployment mywebsite
```

## config maps
## secretes
