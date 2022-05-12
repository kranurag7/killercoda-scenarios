> kyverno is a kubernetes native policy engine. 

`
kubectl create -f https://raw.githubusercontent.com/kyverno/kyverno/main/config/install.yaml
`{{exec}}
- Make sure you have kyverno installed 
- Execute the command 
  
`kubectl get ns`{{exec}}

- If you see the `kyverno` namespace then kyverno is installed properly.

--- 

- Just to be extra sure that everything is working properly execute 
`kubectl -n kyverno get all`{{exec}}
- Everything should be running and if not Happy Troubleshooting. 
- I hope everything is working fine. 



- Kyverno gets installed as dynamic admission controller so let's check the webhooks.
- Check validating webhooks 

`
kubectl get validatingwebhookconfigurations.admissionregistration.k8s.io
`{{exec}}
- We can see that kyverno has created some validating webhooks in the cluster. 
- Check mutating webhooks

`
kubectl get mutatingwebhookconfigurations.admissionregistration.k8s.io
`{{exec}}

 
