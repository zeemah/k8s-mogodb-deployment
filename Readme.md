# Deploy mongodb & mongo-express on k8s

## step 1 - deploy mongo-secret.yaml 

    "kubectl apply -f mongo-secret.yaml"

## step 2 - deploy mongo.yaml

    "kubectl apply -f mongo.yaml "

use "kubectl describe pod <pod-name>" to get details/progress of pod.

Note: if docker image size is large, you'll get an error "error: code = unknown desc = conext deadline exceeded"
    this means that kubectl timed out and the image wasn't downloaded. 

FiX: to fix this, download to minikube first using:

    "minikube ssh docker pull <image-name>"

    then "kubectl delete -f <mongo.yaml>" to delete 
    finally "kubectl apply -f mongo.yaml" and it should work
    use "kubectl get pods" to confirm 

## step 3 - deploy mongo-configmap.yaml

    "kubectl apply -f mongo-congifmap.yaml"

## step 4 - deploy mongo-express.yaml

    "kubectl apply -f mongo-express.yaml"

## step 5 - assign ip to loadbalancer service/external service

    "minikube service <service-name>"
    
    This will open mongo express DB on your web browser. 
