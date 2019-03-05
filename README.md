# redash-helm GKE Installation
Follow the steps below to deploy redash multi-nodes on GKE

## Create a GKE cluster

## Configure kubectl in CLI
```
gcloud config set project {project-id}
gcloud container clusters get-credentials {cluster-id} --zone {zone-id} --project {project-id}
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
