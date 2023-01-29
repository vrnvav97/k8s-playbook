# k8s-playbook

More Desciption on Pod can be found at https://medium.com/@vrnvav97/pods-in-kubernetes-c4f384bbf5fb

# Getting Started

1. Get a Kubernetes Cluster Setup
2. Clone this git repo with branch feature/pod
3. To Deploy Nginx image within pod run below command
```
kubectl apply -f nginx-pod.yaml
```
4. To Deploy Alpine image within pod run below command
```
kubectl apply -f alpine-pod.yaml
```
5. To get Descriptive output, run below describe command, same can be found in *-output.txt
```
kubectl describe pod nginx-pod
kubectl describe pod alpine-pod
```