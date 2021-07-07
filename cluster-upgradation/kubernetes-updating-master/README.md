# Pre-Requisites
    Create Cluster with 1.17 or 1.18
# Upgrade ````control plane```` using below command
    eksctl upgrade cluster --name eksdemo  --region us-east-1 --approve
# Check components of cluster under kube-system namespace
    kubectl get pods -n kube-system
  ![image](https://user-images.githubusercontent.com/58024415/124728371-2ad42280-df2d-11eb-9eeb-31249ad6d83d.png)

  Need to upgrade above components ````kube-proxy, aws-node, coredns````
# Write Utils in kube-config file with latest version of cluster   
    eksctl utils write-kubeconfig --cluster eksdemo --region us-east-1
# Upgrade ````kube-proxy````
    eksctl utils update-kube-proxy --cluster eksdemo --region us-east-1 --approve
# Upgrade ````aws-node````
    eksctl utils update-aws-node --cluster eksdemo --region us-east-1 --approve
# Upgrade ````coredns````
    eksctl utils update-core-dns --cluster eksdemo --region us-east-1 --approve
# Next need to be done node-group upgradation
  [node-group upgradation](https://github.com/Naresh240/kubernetes/tree/main/cluster-upgradation/kubernetes-updating-nodegroup)