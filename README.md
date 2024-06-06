# WrenAi-k8s
Deployment of WrenAi app in your K8s using ArgoCD

The main ArgoCD app [wrenai.app.yaml located here](all-apps-infra/wrenai.app.yaml)

The main [kustomization folder](infra-deployments/wrenai/kustomizations) located here.

You will need to modify the Secret, Ingress and Certificate manifests in the [examples](infra-deployments/wrenai/kustomizations/examples) folder. And also the [ConfigMap kustomization patch](infra-deployments/wrenai/kustomizations/patches/cm.yaml) file in the patches folder.

Modify the example of the secrets manifest first before applying the main kustomization. Do not include Secter manifest into your ArgoCD repo. Best practice is not to store your password in your git repo!

```
vi infra-deployments/wrenai/kustomizations/examples/secret-wren_example.yaml
kubectl apply -f infra-deployments/wrenai/kustomizations/examples/secret-wren_example.yaml
```

Check the resulting manifests inflated by kustomization tool before you apply them to yuor k8s cluster:
```
kubectl kustomize infra-deployments/wrenai/kustomizations --enable-helm > infra-deployments/wrenai/kustomizations/wrenai.kustimized.yaml
```
