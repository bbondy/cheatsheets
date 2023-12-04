Setup Google Cloud Platform (GCP) kubernetes instance:  

```
# Set a default zone
gcloud config set compute/zone us-west1-a

# Create a cluster (must have Kubernetes Engine API enabled, otherwise the command will fail and tell you how to enable it)
gcloud container clusters create kuar-cluster --num-nodes=3

# Get credentials for the cluster
gcloud container clusters get-credentials kuar-cluster
```

Restful path:  
Each Kubernetes object exists at a unique Restful HTTP path;
Each object is represented as a JSON or yaml file.

The kubernetes client is:  
kubectl for interacting with the Kubernetes API
Used to manage most Kubernetes objects, such as Pods, ReplicaSets, and Services.


YAML or JSON files to create, update, or delete objects on the Kubernetes server:  
Create or apply if different:  
`kubectl apply -f obj.yaml # The resource type is obtained from the yaml`

`--dry-run` can be passed to see which changes would be made  
Delete an object:  
`kubectl delete -f obj.yaml`

Delete an object using resource type and name:  
`kubectl delete <resource-name> <obj-name>`

Getting logs to debug:  
`kubectl logs <pod-name>`

Version of local kubectl tool and version of Kubernetes API server:   
`kubectl version`

Example output:  
  
> Client Version: v1.28.2  
> Kustomize Version: v5.0.4-0.20230601165947-6ce0bf390ce3  
> Server Version: v1.27.3-gke.100  
  
To get general diagnostics:  
`kubectl get componentstatuses`


Get running nodes:  
`kubectl get nodes`

Get information about a specific node:  
`kubectl describe nodes kube1`


Deploy deployment and service manifest to your kubernetes cluster:  
Deploy: `kubectl apply -f deployment.yaml`
Expose: `kubectl apply -f service.yaml`

Check everything is running correctly:   
Get Deployments: `kubectl get deployments`  
Get Pods: `kubectl get pods`  
Get Services: `kubectl get services`  
Can also be combined: `kubectl get pods,services`  
To get more detailed info about a particular object: `kubectl describe <resource-name> <obj-name>`  
Supported fields for a Kubernetes object: `kubectl explain pods`  
Watch changes over time: `kubectl get pods --watch`  

Execute a command in a running instance:  
`kubectl exec -it <pod-name> -- bash`

Copy files to and from a pod:  
`kubectl cp <pod-name>:</path/to/remote/file> </path/to/local/file>`

Forward traffic from local machine on port 8080 to remote container on port 80  
`kubectl port-forward <pod-name> 8080:80`

View kubernetes events:  
`kubectl get events`

See how the cluster is using resources (machine level):  
`kubectl top nodes`

See how the pods usage (application level):  
`kubectl top pods`

Stop future pods from being scheduled onto that machine:  
`kubectl cordon`

Re-enable pod scheduling on the node:  
`Kubectl uncordon`

Remove any pods that are currently running on that machine:  
`kubectl drain`

Vscode plugin:  
https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-kubernetes-tools

Send input to the running process:  
`kubectl attach -it <pod-name>`

Namespaces:  
Namespaces are like folders to organize objects in the cluster  
kubectl takes these command line parameters:  
```
--namespace=mystuff
--all-namespaces
```

Contexts:  
To change a namespace, user, and clusters more permanently, use contexts.  
Contexts live on the filesystem usually in:  
` ~/.kube/config`

Creating a new context with a different context  
`kubectl config set-context my-context --namespace=mystuff`

And to change the current context:  
`kubectl config use-context my-context`

Using JSONPath to extract the IP address of a specified pod:  
`kubectl get pods my-pod -o jsonpath --template={.status.podIP}`
