# k3k-bgp
BGP routing for k3k virtual mode clusters.
Host cluster is RKE2 cluster with Calico CNI.

<img width="641" height="377" alt="image" src="https://github.com/user-attachments/assets/ade4332a-0beb-4351-a546-859786f95da6" />

# Host Cluster 
1) Deploys frr-k8s - host-cluster/frr/fleet.yaml
2) BGP Peering to K3k clusters - As k3k node will have dynamic IP, dynamic BGP is configured - host-cluster/bgp-config/k3k-dynamic-peers.yaml
3) BGP Peering to upstream router - host-cluster/bgp-config/upstream.yaml

# Virtual Clusters 
1) Deploys frr-k8s - virtual-cluster/frr/fleet.yaml
2) Deploys metallb - virtual-cluster/metallb/fleet.yaml
3) Specific folder under config/overlays/ for each virtual cluster consisting load balancer IP pool in the yaml

Now any service with loadbalancer IP, in any of the virtual clusters will now be reachable from vrouter



#K3k Clusters



<img width="642" height="157" alt="image" src="https://github.com/user-attachments/assets/f77d8262-823e-4926-84ce-7445a197903c" />



#BGP status from Host Cluster



<img width="1255" height="501" alt="image" src="https://github.com/user-attachments/assets/ccb3f8cc-5363-477a-9674-59ec3993989a" />



#IP routes in Host cluster FRR container



<img width="696" height="427" alt="image" src="https://github.com/user-attachments/assets/f3348903-0792-40cc-8798-0ad891e2d154" />



#SVC with LBS in virtual cluster vcl3



<img width="696" height="132" alt="image" src="https://github.com/user-attachments/assets/2381fced-c4ae-4e16-bc23-f5ae5580f9f9" />



#Curl from vRouter to vcl3 service



<img width="886" height="590" alt="image" src="https://github.com/user-attachments/assets/85125378-b10c-4cef-bbd3-17fcca2dcb65" />


