# k8s-playbook

More Desciption on Canary Deployment can be found at https://medium.com/@vrnvav97/canary-deployment-in-kubernetes-a18c81cb9b

# Getting Started

1. Get a Kubernetes Cluster Setup
2. Clone this git repo with branch feature/canary-deployment
3. To Deploy Version V1 of Ninja Game Application, run below command
```
kubectl apply -f v1-deployment.yaml
```
4. Next Step is to attach Service to allow incoming traffic to our version v1 of our application
```
kubectl apply -f ninja-game-service.yaml
```
5. To Validate Creation of Deployment, ReplicaSet, Service and Pod, run
```
kubectl get all
```
6. If any issues faced till this step, debug it using describe command
```
kubectl describe  <object> <object_name>
```
7. By Now, v2 version of application is also tested and docker image is ready with the name ```vrnvav123/ninja-game:v2``` to be deployed
```
kubectl apply -f v2-deployment.yaml
```
8. Time to validate all 8 pods 
```
kubectl get all
```
9. Once all the pods are up and running, its time to test our canary deployment with current weightage of 1:1. For this, we need to create a utility pod, which will be used for testing
```
kubectl apply -f util.yaml
kubectl exec -it util -- bash
```
From within util pod, and watch the results of traffic splitting between v1 and v2 of application equal number of times. This weightage can be changed in this scenario by modifying the number of replicas or routing 100% traffic to single version of application.
```
watch ' curl http://ng-service:80 | grep Ninja Quiz V '
```



# Note:
All the resources are created in default namespace
