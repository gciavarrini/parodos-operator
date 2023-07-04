# parodos-operator


## Deploy
```
kind create cluster

helm install --dependency-update --debug parodos-testing -f parodos-testing/values.yaml --generate-name         
```
