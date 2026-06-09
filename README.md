
Bastion server:
------------------------
```
aws configure
aws eks update-kubeconfig --region us-east-1 --name expense-dev
kubectl get nodes
```

argocd documentation:
https://argo-cd.readthedocs.io/en/stable/
------------------------------------------
```
kubectl create namespace argocd
```
```
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```


k9s:
https://github.com/derailed/k9s
--------------------------------------
Via Webi for Linux and macOS
```
curl -sS https://webinstall.dev/k9s | bash
```


Install Argocd CLI:
https://argo-cd.readthedocs.io/en/stable/cli_installation/

```
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
```
```
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
```
```
rm argocd-linux-amd64
```

https://argo-cd.readthedocs.io/en/stable/getting_started/
```
argocd admin initial-password -n argocd
```
We can open argocd on browser using load balancer service.
username: admin
password: 


argocd.sh
-----------------------------

```
#!/bin/bash

kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64

sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd

kubectl apply -k "github.com/kubernetes-sigs/aws-ebs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-1.47"
```
