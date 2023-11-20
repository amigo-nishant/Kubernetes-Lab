**Use the following commands to interact with and test the pod.yml manifest:**

The pod.yml manifest file defines a Kubernetes Pod named nishant-label with labels indicating it belongs to the "development" environment and has the "pods" class. The Pod runs a single container (c00) with an Ubuntu image, executing a Bash command that continuously echoes "Hello World" every 5 seconds.

1. **Apply the Pod Manifest:**
    
    ```bash
    bashCopy code
    kubectl apply -f pod.yml
    
    ```
    
2. **Check Pod Status:**
    
    ```bash
    bashCopy code
    kubectl get pods
    
    ```
    
    Verify that the **`nishant-label`** Pod is in the "Running" state.
    
3. **View Pod Logs:**
    
    ```bash
    bashCopy code
    kubectl logs nishant-label
    
    ```
    
    Check the logs to see the "Hello World" messages. Press **`Ctrl + C`** to exit.
    
4. **Describe Pod:**
    
    ```bash
    bashCopy code
    kubectl describe pod nishant-label
    
    ```
    
    View detailed information about the Pod, including its labels.
    
5. **Filter Pods by Label:**
    
    ```bash
    bashCopy code
    kubectl get pods -l env=development
    
    ```
    
    List Pods that have the "development" label.
    
6. **Filter Pods by Class Label:**
    
    ```bash
    bashCopy code
    kubectl get pods -l class=pods
    
    ```
    
    List Pods that have the "pods" class label.
    
7. **Clean Up (optional):**
    
    ```bash
    bashCopy code
    kubectl delete pod nishant-label
    
    ```
    
    Delete the Pod to clean up resources.