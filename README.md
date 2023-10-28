## quickstart deployment of k3s cluster

### prerequisites
* 3 x 1gb RAM vps (rancher1, rancher2, rancher3) set up with Ubuntu 22.04LTS
* 20gb block storage volume attached to each node

install k3s on rancher1:
`sudo curl -sfL https://get.k3s.io | sh - --cluster-init`

get join token on rancher1:
`cat /var/lib/rancher/k3s/server/node-token`

join token string will be copy/pasted into \<join-token\> placeholder below  
rancher1 ip address will be copy/pasted into \<rancher1-ip\> placeholder below

install k3s on rancher2
`sudo curl https://get.k3s.io | K3S_URL=https://<rancher1-ip>:6443 K3S_TOKEN=<join-token> sh -s - server`

install k3s on rancher3
`sudo curl https://get.k3s.io | K3S_URL=https://<rancher1-ip>:6443 K3S_TOKEN=<join-token> sh -s - server`
