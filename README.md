# parodos-operator


## Creation
```bash
helmify -f https://github.com/parodos-dev/parodos/releases/download/v1.0.18/manifests.yaml helm-charts/parodos-v1.0.18
helm install --dependency-update --debug parodos-testing -f parodos-testing/values.yaml --generate-name         
```
or 

```bash
make download-manifest
make generate-helmchart
```

Then, 
```bash
 operator-sdk init --plugins helm --domain redhat.com --kind Parodos --helm-chart helm-charts/parodos-v1.0.18
 operator-sdk create api --plugins helm --kind Parodos --helm-chart helm-charts/parodos-v1.0.18
```

```bash
>> operator-sdk init --plugins helm --domain redhat.com --kind Parodos --helm-chart helm-charts/parodos-v.1.0.18
Writing kustomize manifests for you to edit...
Creating the API:
$ operator-sdk create api --kind Parodos --helm-chart helm-charts/parodos-v.1.0.18
Writing kustomize manifests for you to edit...
Created helm-charts/parodos-v.1.0.18
Generating RBAC rules
WARN[0000] Using default RBAC rules: failed to generate RBAC rules: failed to get server resources: Get "https://127.0.0.1:46431/api?timeout=32s": dial tcp 127.0.0.1:46431: connect: connection refused 
```


```bash
>> operator-sdk create api --version v1 --helm-chart helm-charts/parodos-v.1.0.18 

Writing kustomize manifests for you to edit...
Created helm-charts/parodos-v.1.0.18
Generating RBAC rules
WARN[0000] Using default RBAC rules: failed to generate RBAC rules: failed to get server resources: Get "https://127.0.0.1:46431/api?timeout=32s": dial tcp 127.0.0.1:46431: connect: connection refused 

```

## Deploy

To push the docker image
```bash
make docker-build docker-push
```

Then, 
```bash
make install deploy
```