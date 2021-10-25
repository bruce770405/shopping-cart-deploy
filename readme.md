

## Microservice Deploy Demo
![k8s cover](https://github.com/bruce770405/shopping-cart-deploy/blob/main/imgs/cover.png)

* Sample Microservice Apps repository https://github.com/bruce770405/go-shopping-cart
* Minikube https://minikube.sigs.k8s.io/docs/
* istio https://istio.io
* helm https://helm.sh

## minikube start
* minikube start --driver=hyperkit
* minikube addons enable ingress

## istio install
   ```
   $ istioctl install --set profile=demo 
   ```

### helper commands
* use local docker repository when k8s pull images
    ```
    $ eval $(minikube docker-env)
    ```
  
* check istio gateway service
    ```
    $ kubectl get svc istio-ingressgateway -n istio-system
    ```
  
* Automatic Sidecar Injection
    ```
    $ kubectl label namespace <Your_Example Namespace> istio-injection=enabled
    ```

* Manual Sidecar Injection
   ```
   $ istioctl kube-inject -f my-websites.yaml - o my-websites-with-proxy.yaml
   ```
   
