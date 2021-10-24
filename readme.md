## minikube
* minikube start --driver=hyperkit
* minikube addons enable ingress
  
### check istio gateway service
* kubectl get svc istio-ingressgateway -n istio-system

### local repository
* eval $(minikube docker-env)

### istio
* install
   ```
   $ istioctl install --set profile=demo 
   ```  
  
* Automatic Sidecar Injection
  
    ```
    $ kubectl label namespace <Your_Example Namespace> istio-injection=enabled
    ```

* Manual Sidecar Injection

   ```
   $ istioctl kube-inject -f my-websites.yaml - o my-websites-with-proxy.yaml
   ```
   