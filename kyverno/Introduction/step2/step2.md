- What is a policy? 
- A policy in simple terms is a contract between two different entities. Policies are important to have in your organisation/k8scluster to enforce best practices. 

- You can set the scope of the policy either to namespace level(Policy) or clusterlevel(ClusterPolicy). 

- Let's deploy a policy in our k8s cluster 
- We will deploy a policy that will check if the pods have requests and limits set or not. If not then it will deny the request. 
```
kubectl create -f- << EOF
apiVersion: kyverno.io/v1
kind: ClusterPolicy
metadata:
  name: require-limits-and-requests
spec:
  validationFailureAction: enforce
  rules:
    - name: validate-resources
      match: 
        resources:
          kinds:
            - Pod
      validate:
        message: "You need to set request and limits in the manifest"
        pattern:
          spec:
            containers:
            - resources:
                requests:
                  memory: "?*"
                  cpu: "*?"
                limits:
                  memory: "?*"
                  cpu: "?*"
EOF
```
- Now check if the the cluster policies are created properly. 
- Run the command 

`kubectl get cpol` 
- cpol here stands for clusterpolicies. 
- Now we have deployed our first policy. Go through the manifest of the policy and you'll understand that this policy is set in enforce mode and it will block the request if limits and requests are not set. 

