# MinIO deployment on Kind cluster

## Kind Cluster

How to inicialize the kind cluster using the [kind.yml](kind.yml) file.
```bash
kind create cluster --name minio --config kind.yml --kubeconfig ~/.kube/kind.yml
```

Export the environment variable `KUBECONFIG` to access the cluster.
```bash
export KUBECONFIG="~/.kube/kind.yml
```

Verify if cluster respond Ok.
```bash
kubectl cluster-info
```

And install the CNI [`weave-net`](https://www.weave.works/docs/net/latest/kubernetes/kube-addon/).
```bash
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
```
After that, the nodes will be ready. :y:

Check with:
```bash
kubectl get nodes
kubectl get pods --all-namespaces
```

## MinIO

Command to deployment `minIO`.
```bash
kubectl create --filename minio/
```
