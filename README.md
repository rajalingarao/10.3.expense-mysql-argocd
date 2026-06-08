# 10.2.expense-mysql-argocd



# EBS Dynamic Provisioning  Steps:
1. We need to install the EBS CSI drivers in EKS cluster.
   kubectl apply -k "github.com/kubernetes-sigs/aws-ebs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-1.32"
2. Your nodes should have access to connect with EBS volumes. Attach EBS CSI policy to the EC2 instance role.
3. someone on behalf of you should create EBC Volume in AWS and equivalent PV in K8s automatically --> dynamic provisioning that one is Storage class.

$kubectl get sc
$kubectl api-resources

$kubectl get pods
$kubectl exec -it ebs-dynamic-nginx-pod -- bash
$cd /usr/share/nginx/html/
$echo "<h1>Hello from EBS Dynamic volumes</h1>" > index.html