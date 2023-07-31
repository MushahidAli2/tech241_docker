# K8 DEPloyment
1. Nginx
```yml
apiVersion: apps/v1 # which API to use for deployment
kind: Deployment # pod - service what kind of service you want to create
# what would you like to call it - name the service/object
metadata:
  name: nginx-deployment # naming the deployment
spec:
  selector:
    matchLabels:
      app: nginx #look for this label to match with k8 service
    # let's create a replica set of this with instances/pods
  replicas: 3 # 3 pods
    # template to use it's label for k8 service to launch in the browser
  template:
    metadata:
      labels:
        app: nginx # this label connects to the service or any other k8 components
  # let's define the container spec
    spec:
      containers:
      - name: nginx
        image: # use the image that you built
        ports:
        - containerPort: 80

# create a kubernetes nginx-service.yml to create a k8 servicekub
```
2. Nginx service:
```yml 
---
# select the type of API version and type of service
apiVersion: v1
kind: Service
#Metadata for name
metadata:
  name: nginx-svc
  namespace: default  # sre
# Specification to include ports Selector to connect to the deployment
spec:
  ports:
  - nodePort: 30001 # range is 30000 - 32768
    port: 80
    targetPort: 80

# Let's define the selector and label to connect to nginx deployment
  selector:
    app: nginx

  # Creating NodePort of deployment
  type: NodePort # alse use LoadBalancer - for local use ClasterIP
```
3. Node
```yml
apiVersion: apps/v1 # which API to use for deployment
kind: Deployment # pod - service what kind of service you want to create
# what would you like to call it - name the service/object
metadata:
  name: node-deployment # naming the deployment
spec:
  selector:
    matchLabels:
      app: node #look for this label to match with k8 service
    # let's create a replica set of this with instances/pods
  replicas: 3 # 3 pods
    # template to use it's label for k8 service to launch in the browser
  template:
    metadata:
      labels:
        app: node # this label connects to the service or any other k8 components
  # let's define the container spec
    spec:
      containers:
      - name: node
        image: mushahid12/tech241-sparta-app # use the image that you built
        ports:
        - containerPort: 3000

# create a kubernetes nginx-service.yml to create a k8 servicekube
```
4. Node service
```yml
---
# select the type of API version and type of service
apiVersion: v1
kind: Service
#Metadata for name
metadata:
  name: node-svc
  namespace: default  # sre
# Specification to include ports Selector to connect to the deployment
spec:
  ports:
  - nodePort: 30002 # range is 30000 - 32768
    port: 3000
    targetPort: 3000

# Let's define the selector and label to connect to nginx deployment
  selector:
    app: node

  # Creating NodePort of deployment
  type: NodePort # alse use LoadBalancer - for local use ClasterIP
```
`kubectl create -f <filename>` - creating a k8 deployment from the yml file we created

`kubectl get deployment` - check deployments running

`kubectl get pods` - check pods running

After writing a yml file we need to create services:

```
kubectl create -f nginx-service.yml
kubectl create -f node-service.yml
```