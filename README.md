pods: runs one or more closely related containers.  Runs a single set of containers, good for one-off dev proporses, rarely used directly in production
Services: Sets up networking in Kubernates cluster
Deployment: Maintains a set of identical pods, ensuring that they have the correct config and that the right number exists. Runs a set of identical pods (one or more), monitors the state of each pod, updating as necessary, good for dev, good for production


--feed a config file to kubectl
kubectl apply -f <filename>

-- print the status of all running pods
kubectl get <pods|services|deployments> -o wide
-o wide añade columnas extra, incluyendo la ip

-- access to our pod: easy cause we are using docker kubernates
localhost:31515

--- get detail info about an object or object type
kubectl describe <objectType> <objectName>

--Remove an object (imperative order)
kubectl delete -f <configFile>

Update image version:
-Change deployment to use multi-client again
-update the multi-client image, push to Docker Hub
-get the deployment to recreate our pods with the lattest version of multi-client

imperative command to update a docker image
kubectl set <propertyName> <objectType>/<objectName> <containerName> = <New property>
kubectl set image deployment/client-deployment client=eggop1992/multi-client:v5

-- para mirar los logs de un container de un pod
kubectl logs <pod_id> 
-- para abrir un shell en el container de un pod
kubectl exec -it <pod_id> sh 


---- para quien usa minicube en lugar de docker k8
-- cambia docker client para que apunte al docker server de minicube en lugar del de la instalacion de win, solo para la session de la consola
eval $(minikube docker-env)