# kubectl-eks-container
Dockerfile for building kubectl with awscli to work with EKS

I use Windows WSL with kubernetes locally, which uses the latest Kubernetes dev stack .I stopped wasting resources with hyper-v and other emulations.  When I needed to manage an EKS cluster from the same WSL I was informed that the versions conflict. "
error: exec plugin: invalid apiVersion "client.authentication.k8s.io/v1alpha1"

Using this file builds a container that will allow you to run kubectl of your favorite version, just change the first line to represent the version you want. It is really designed to use with EKS.

MIT License - Use at your own risk

Here is the gist of how to use this 
$ docker build -t charmingsteve/kubectleks:1.21_v_02 -f Dockerfile-kubectl-awscli .

$ docker run  -it  --rm  -v /home/steve/.kube-eks:/root/.kube -v /home/steve/.aws:/root/.aws  charmingsteve/kubectleks:1.21_v_02 -c "aws eks update-kubeconfig --region us-east-2 --name eks-autoscaling"

$ docker run  -it  --rm  -v /home/steve/.kube-eks:/root/.kube -v /home/steve/.aws:/root/.aws  charmingsteve/kubectleks:1.21_v_02 -c "kubectl get svc"
