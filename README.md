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
