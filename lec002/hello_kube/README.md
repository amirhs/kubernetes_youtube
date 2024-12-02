To build the Docker image, run the following command:

This command creates a local image named `hello_kube` with the tag version `1.0.0`.

```sh
docker buildx build -t hello_kube:1.0.0 .
```

The following command tags the local image with your remote registry username, making it ready to push to the repository. Please replace `aaghamohammadi` with your current registry username for the following commands.

```sh
docker tag hello_kube:1.0.0 aaghamohammadi/hello_kube:1.0.0
```

Make sure you log in to your registry in order to push the image.

```sh
docker push aaghamohammadi/hello_kube:1.0.0
```


You can run a simple Pod using an imperative command, although it is not recommended. In the future, we will learn other ways (i.e., declarative) to run pods.

The following command runs a pod named `hello-kube` with a single container in it. The restart policy for the pod is determined by the `--restart` flag. Legal values are `["Always", "OnFailure", "Never"]`. The default value is `"Always"`.

```sh
kubectl run hello-kube --image=aaghamohammadi/hello_kube:1.0.0 --restart=Never
```

You can list all the pods in the current cluster using:

```sh
kubectl get pods
```

The `describe` command shows details of a specific resource like a pod. It provides detailed information about a single pod, including its IP address and the node it is running on.

```sh
kubectl describe pod hello-kube
```

To get the full JSON output of a pod, you can use the following command. This is useful for debugging and understanding the pod's configuration and status in detail.

```sh
kubectl get pod hello-kube -o json
```

Kubectl can forward traffic from a node to a Pod, which is a quick way to communicate with a Pod from outside the cluster.

```sh
kubectl port-forward pod/hello-kube 8080:80
```

Now, browse to `localhost:8080` in your browser.

To remove the pod and return your Kubernetes environment to a clean state, you can use the following command:

```sh
kubectl delete pod hello-kube
```
