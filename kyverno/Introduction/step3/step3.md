- In the previous section we have created a policy named `require-limits-and-requests`
- It's time to see that in action. 
- Create a pod without request and limits set. 

`kubectl run my-pod --image=nginx:alpine` 

- You will see the following error.

```
Error from server: admission webhook "validate.kyverno.svc-fail" denied the request: 

resource Pod/default/my-pod was blocked due to the following policies

require-limits-and-requests:
  validate-resources: 'validation error: You need to set request and limits in the
    manifest. Rule validate-resources failed at path /spec/containers/0/resources/limits/'
```
- So we have seen that our policy is effective and denying the request of pods which is not having limits and requests set. 
- Now let's try to deploy a pod manifest which have request and limits set. 

```
kubectl create -f- << EOF
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:alpine
    ports:
    - containerPort: 80
    resources:
      requests:
        memory: "64Mi" # 64Mi (binary notation)
        cpu: "250m" # 250 millicores
      limits:
        memory: "128Mi"
        cpu: "500m"
EOF
```
- Now you will see that our pod is up and running now. 
- To check if your pod is runnnig 

`kubectl get pods`{{exec}}

