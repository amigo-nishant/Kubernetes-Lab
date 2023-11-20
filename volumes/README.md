**Use the following commands to interact with and test the pod.yml manifest:**

This configuration essentially creates a shared temporary directory (/tmp/xchange) between the two containers (c1 and c2) within the same pod. Any data written by one container to this shared directory will be visible to the other container.

To test the shared **`emptyDir`** volume configuration from both containers (**`c1`** and **`c2`**), you can follow these steps:

1. Apply the YAML manifest to create the Pod:
    
    ```bash
    kubectl apply -f pod.yml
    ```
    
2. Verify that the Pod is running:
    
    ```bash
    kubectl get pods
    ```
    
    Ensure that the **`myvolemptydir`** Pod is in the "Running" state.
    
3. Access the shell of the first container (**`c1`**):
    
    ```bash
    kubectl exec -it myvolemptydir -c c1 -- /bin/bash
    ```
    
    This command opens an interactive shell in the **`c1`** container within the **`myvolemptydir`** Pod.
    
4. Inside the **`c1`** container's shell, create a file in the mounted volume:
    
    ```bash
    echo "Hello from c1" > /tmp/xchange/testfile.txt
    ```
    
    This command creates a file named **`testfile.txt`** with the specified content in the shared volume.
    
5. Exit the **`c1`** container's shell:
    
    ```bash
    exit
    ```
    
6. Access the shell of the second container (**`c2`**):
    
    ```bash
    kubectl exec -it myvolemptydir -c c2 -- /bin/bash
    ```
    
    This command opens an interactive shell in the **`c2`** container within the **`myvolemptydir`** Pod.
    
7. Inside the **`c2`** container's shell, check if the file created by **`c1`** is visible:
    
    ```bash
    cat /tmp/data/testfile.txt
    ```
    
    This command displays the contents of the file. If successful, you should see "Hello from c1."
    
8. Exit the **`c2`** container's shell:
    
    ```bash
    exit
    ```
    

These commands demonstrate the basic testing of the shared **`emptyDir`** volume configuration. Data written by one container is accessible to the other container in the same pod. Keep in mind that the data in the **`emptyDir`** volume is ephemeral and will be lost if the pod is removed from the node.

1.  To delete the Pod and the associated volume, you can use the following command:

```bash
kubectl delete pod myvolemptydir
```

This command will delete the **`myvolemptydir`** Pod, and since the volume (**`emptyDir`**) is part of the pod, the volume will be removed as well.