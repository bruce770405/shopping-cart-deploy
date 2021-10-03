
istio
* Automatic Sidecar Injection
  
    kubectl label namespace <Your_Example Namespace> istio-injection=enabled

* Manual Sidecar Injection

    istioctl kube-inject -f my-websites.yaml - o my-websites-with-proxy.yaml