# wireguardaks

1- register custom node config to allow unsafe sysctl https://docs.microsoft.com/en-us/azure/aks/custom-node-configuration

https://docs.linuxserver.io/images/docker-wireguard
https://docs.microsoft.com/en-us/azure/aks/custom-node-configuration

- start the process:
1- Create LB service (get the public ip)

use wireservice.yaml


2- create the pvc from yaml

use wirepvc.yaml

3- create the deployment

wiredeploy.yaml
