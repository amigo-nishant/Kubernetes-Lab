**Use the following commands to interact with and test the pod.yml manifest:**


The two manifest files define separate Kubernetes Pods:

testpod Pod:
Container c00 runs an NGINX image and exposes port 80 for incoming network traffic.
testpod2 Pod:
Container c01 runs an Apache HTTP Server (httpd) image and also exposes port 80 for incoming network traffic.
These two Pods are independent of each other and are not explicitly linked or connected. Each Pod runs its own set of containers with specified configurations. If you need communication or interaction between these Pods, you might consider using Services or other Kubernetes networking features.

### **For `testpod` with Nginx:**

```
kubectl apply -f pod.yml
kubectl port-forward testpod 8080:80
```

This command forwards local port 8080 to port 80 in the **`testpod`** Pod. Now, you can access Nginx from your local machine using **`http://localhost:8080`**.

### **For `testpod2` with Apache HTTP Server:**

```
kubectl apply -f pod2.yml
kubectl port-forward testpod2 8081:80
```

This command forwards local port 8081 to port 80 in the **`testpod2`** Pod. Now, you can access Apache HTTP Server from your local machine using **`http://localhost:8081`**.

Ensure that the ports you choose for local forwarding (8080 and 8081 in these examples) are available and not in use by other applications on your machine.