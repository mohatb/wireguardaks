# wireguardaks

1- register custom node config to allow unsafe sysctl (you need to create a new cluster or a new nodepool with custom config).
https://docs.microsoft.com/en-us/azure/aks/custom-node-configuration

2- Create LB service to expose udp 51820 which will be used by wireguard clients (get the External ip)

use wireservice.yaml
```
kubectl apply -f wireservice.yaml
kubectl get service wireguard-service -n wireguard
```

3- create a pvc to store wireguard data using wirepvc.yaml

```
kubectl apply -f wireservice.yaml
```

4- edit the deployment wiredeploy.yaml and update the environment variables:

```
TZ: timezone
SERVERURL: <external ip exposed by the LB service>
PEERDNS: <DNS Server IP> # can be set to coredns ip.
ALLOWEDIPS: <this is the network clients will be able to access> #you can set this to the vnet subnet. if peerdns is outside this range, you may want to set it also.
#example: 
#ALLOWEDIPS: 10.244.1.0/24, 10.0.0.10/32
INTERNAL_SUBNET: <this will be used by the clients and the wireguard pod, better not to conflict with allowed ips from the vnet.>

```




References:<br>
https://docs.linuxserver.io/images/docker-wireguard<br>
https://docs.microsoft.com/en-us/azure/aks/custom-node-configuration
