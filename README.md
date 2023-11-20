# Kubernetes-Lab
Hands-on-Lab 

- Create or apply the Pod using **`kubectl apply`**:
    
    ```bash
    kubectl apply -f pod1.yml
    ```
    
- View information about the Pod:
    
    ```bash
    kubectl get pod testpod
    ```
    
- Describe the Pod for more details:
    
    ```bash
    kubectl describe pod testpod
    ```
    
- Retrieve the logs from the container in the Pod:
    
    ```bash
    kubectl logs testpod -c c00
    ```
    
- Execute a command in the container:
    
    ```bash
    kubectl exec -it testpod -c c00 -- /bin/bash
    ```
    
- Delete the Pod::
    
    ```bash
   kubectl delete pod testpod
    ```
