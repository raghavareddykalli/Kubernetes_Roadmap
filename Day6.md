#Kubernetes Ingress

https://outshift-headless-cms-s3.s3.us-east-2.amazonaws.com/blog/k8s-ingress/ingress-fanout-1.png

## Why Ingress?

Kubernetes Services offer basic features like load balancing, service discovery, and exposing applications, but lack advanced load balancing features such as:

•Ratio-based routing

•Sticky sessions

•Host and path-based routing

Also, using the LoadBalancer service type for every app results in high cloud provider costs due to multiple public IP allocations.

## Problems Solved by Ingress

•One LoadBalancer/IP for multiple services.

•Advanced routing capabilities (host/path/TLS).

•Wildcard routing.

•Lower cost by reducing cloud IP allocations.

## Ingress Architecture

•Users define Ingress resources via YAML.

•Load balancing vendors (NGINX, HAProxy, Traefik, etc.) create Ingress Controllers.

•Controllers watch Ingress resources and configure routing accordingly.

•Deployed using Helm or manifest files and run as pods in the cluster.

## Installation

•**On Minikube**:

```minikube addons enable ingress```

•**On other clusters**: Use vendor documentation (NGINX, HAProxy, Ambassador, etc.)

## Demo 

•Install ingress using above step.

.Create a ingress.yaml file from documentation and edit necessary steps like changing name, host name, service name and port.

```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ingress-example
spec:
  rules:
  - host: "foo.bar.com"
    http:
      paths:
      - pathType: Prefix
        path: "/bar"
        backend:
          service:
            name: my-service
            port:
              number: 80
```

•Create ingress using below command

  ```kubectl apply -f ingress.yaml```
 
•Now we have to install ingress controller. Search for your specific ingress controller and download it.

•For demo purpose, let me take nginx ingress controller.

•Use the below command to enable nginx ingress controller.

 ```minikube addons enable ingress```

•For production level we use existing domains like amazon.com but here we used foo.bar.com and we cant purchase a domain for demo.

•Get the minikube ip address.

•For that, map this domain to ip address in /etc/domains file.

•Now when we ping this domain we get the response. 



 
