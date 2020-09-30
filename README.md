### update AWS CLI
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
which aws
sudo ./aws/install --bin-dir /usr/bin --install-dir /usr/bin/aws-cli --update
```
### configure AWS
```
aws configure
```
### install KubeCtl
```
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version --client
```
### install EKSCtl
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```

### install git

```
sudo yum install git -y
```

### Clone This repo
```
git clone https://github.com/misterjacko/k8s-practice.git
```

### deploy cluster

```
eksctl create cluster --name=TestCluster --version=1.16 --zones=us-east-1a,us-east-1b,us-east-1c --nodegroup-name=worker-node --node-type=t3.small --nodes=3 --managed
```
### config cluster
```
aws eks --region us-east-1 update-kubeconfig --name TestCluster
```

### Deployment

```
kubectl apply -f nginx-deploy.yml
```