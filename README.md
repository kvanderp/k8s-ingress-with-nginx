# k8s-ingress-with-nginx

In order to get access to rgistry.gitlab.com, log in first.

docker login registry.gitlab.com

Next, create a k8s secret which will be used to authneticate to gitlab. Change username in the path below as required

kubectl create secret generic regcred \
>     --from-file=.dockerconfigjson=/home/k8sadmin/.docker/config.json \
>     --type=kubernetes.io/dockerconfigjson

For ingress controller, first create RBAC, Common resources, CRD's.
https://docs.nginx.com/nginx-ingress-controller/installation/installation-with-manifests/


Create Secret for ingress controller (in nginx-ingress namespace):

kubectl create secret generic regcred --from-file=.dockerconfigjson=/home/k8sadmin/.docker/config.json --type=kubernetes.io/dockerconfigjson --namespace="nginx-ingress"
