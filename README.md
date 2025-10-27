# minikube_demo

Following "Kubernetes Crash Course for Absolute Beginners" by Nana Janashia

## About

This repo contains the files that I produced when following the youtube video [Kubernetes Crash Course for Absolute Beginners [NEW]](https://www.youtube.com/watch?v=s_o8dwzRlu4) from TechWorld with Nana.

## Contents
* mongo-config.yaml
* mongo-secret.yaml
* mongo.yaml
* webapp.yaml

## Getting started

To get this running on my mac, I used Macports.  
Using the Macports CLI:

```
sudo port selfupdate
sudo port upgrade outdated
sudo port install minikube
```
And optionally:
```
sudo port install qemu
```

## Resources

* [Kubernetes Documentation](https://kubernetes.io/docs/home/)
* [Nana's k8s-demo Image](https://hub.docker.com/r/nanajanashia/k8s-demo-app)

## Running the system

Start minikube with automatic configuration:
```
minikube start
```
Check minikube status
```
minikube profile list
```
Check minikube node status
```
kubectl get node
```
Or for a more informative result:
```
kubectl get node -o wide
```
Start the `configmap` that names the mongo service:
```
kubectl apply -f mongo-config.yaml
```
Start the `secret` that handles the mongo username and password:
```
kubectl apply -f mongo-secret.yaml
```
Start the `deployment` of the mongo pod:
```
kubectl apply -f mongo.yaml
```
Start the `deployment` of the webapp pod:
```
kubectl apply -f webapp.yaml
```

## Check system status

Once you have started teh configmap, secret, and two deployments, try these to check the status of the kubernetes system:
```
kubectl get all
kubectl get configmap
kubectl get pod
```
Then, using the service and pod names returned:
```
kubectl describe service webapp-service 
kubectl describe pod <webapp-deployment name from get pod result>
kubectl logs <webapp-deployment name from get pod result>
```

## Connect to the webapp from a browser

First find the ip of the minikube system:
```
minikube ip
```
Then use the ip address in your browser:
```
http://<minikube ip>:30100
```


