# wireguardaks

1- register custom node config to allow unsafe sysctl (you need to create a new cluster or a new nodepool with custom config).
https://docs.microsoft.com/en-us/azure/aks/custom-node-configuration

2- Create LB service (get the public ip)

use wireservice.yaml
```
kubectl apply -f wireservice.yaml
```



3- create the pvc from yaml

use wirepvc.yaml

4- create the deployment

wiredeploy.yaml

Ref:
https://docs.linuxserver.io/images/docker-wireguard
https://docs.microsoft.com/en-us/azure/aks/custom-node-configuration
