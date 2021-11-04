

## Microservice Deploy Demo
![k8s cover](https://github.com/bruce770405/shopping-cart-deploy/blob/main/imgs/kubernetes-horizontal-color.png)

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
  
## helm commands
* install
  ```
  $ helm install -n {namespace-name} {helm-chart-name} . -f ./values.yaml
  ```
* upgrade
  ```
  $ helm upgrade -n {namespace-name} {helm-chart-name} . -f ./values.yaml
  ```

## another maybe useful
* minikube demo use
   ```
   $ export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].nodePort}')
   $ export INGRESS_HOST=$(minikube ip)
   $ minikube tunnel
   $ export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT
   ```
