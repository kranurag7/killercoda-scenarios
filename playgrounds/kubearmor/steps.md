- You will use kubearmor CLI a.k.a `karmor` to install kubearmor in your cluster. 

- Execute the command below to install `karmor` 

```
curl -sfL http://get.kubearmor.io/ | sudo sh -s -- -b /usr/local/bin
```{{exec}}

- Verify the `karmor` installation 

```
karmor version
```{{exec}}

- Install kubearmor in your cluster using `karmor install` 

```
karmor install
```{{exec}}

- Wait for 1-2 minutes until all pod starts running. 

- Check whether kubearmor components are running or not. 

```
kubectl -n kube-system get pods,svc,ds 
```{{exec}}

- Refer to [this](https://docs.kubearmor.com/kubearmor/getting-started/deployment_guide) guide in order to deploy some sample application and policies. 