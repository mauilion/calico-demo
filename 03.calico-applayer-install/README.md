### Install the application layer policy stuff.

Docs are here: https://docs.projectcalico.org/master/getting-started/kubernetes/installation/app-layer-policy

tldr;

```
kubectl apply -f https://docs.projectcalico.org/master/getting-started/kubernetes/installation/manifests/app-layer-policy/kubernetes-datastore/calico-networking/calico-node.yaml
```

then install istio:

```
curl -L https://git.io/getLatestIstio | ISTIO_VERSION=1.0.7 sh -
kubectl apply -f istio-*/install/kubernetes/helm/istio/templates/crds.yaml
kubectl apply -f istio-*/install/kubernetes/istio-demo-auth.yaml
```

fixup the istio sidecar injection:

```
kubectl apply -f \
https://docs.projectcalico.org/master/getting-started/kubernetes/installation/manifests/app-layer-policy/istio-inject-configmap.yaml
```

Adding Calico Auth services to the istio mesh:

```
kubectl apply -f \
https://docs.projectcalico.org/master/getting-started/kubernetes/installation/manifests/app-layer-policy/istio-app-layer-policy.yaml
```

** SUPER IMPORTANT **

Label your namespaces where you are going to deploy stuff for example:

```
kubectl label namespace default istio-injection-enabled
```


