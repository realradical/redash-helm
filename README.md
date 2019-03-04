# redash-helm GKE Installation

## Create a GKE cluster

## Configure kubectl in CLI
```
gcloud config set project {project-id}
gcloud container clusters get-credentials {cluster-id} --zone {zone-id}
```
## Install helm chart
```
sudo snap install helm --classic
```

## Initialize helm chart
```
helm init
kubectl create serviceaccount --namespace kube-system tiller
kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
kubectl patch deploy --namespace kube-system tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'
```
## Deploy helm chart
```
helm install .
```
