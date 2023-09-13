Step 1: git clone https://github.com/vishswati1011/kube-network.git

Step 2: run run the project 

    $ docker-compose up -d --build 

in this project we create multiple deployment container and will comminicate between pod    

First cd users-api

then create image users-api $ docker build -t appdockers/kube-network .

then push $ docker push appdockers/kube-network

now will create kubernetes folder and create file

users-deployment.yaml 


apiVersion: apps/v1

kind: Deployment

metadata:

  name: users-deployment

spec:

  replicas: 1

  selector:

    matchLabels:

      app: users

  template:

    metadata:

      labels:

        app: users

    spec:

      containers:

        - name: users

          image: appdockers/kube-net-users

  then we will apply it 

  $ minikube start

  cd ..

  cd kubernetes
  
  $ kubectl apply -f=users-deployment.yaml         

  video 229  Another Look ar services

  create users-service.yaml file

apiVersoin: v1
kind: Service
metadata:
  name: users-service
spec:
  selector:
    app: users  # its a label name which in confgure in users-deployment.yaml file 
  type: LoadBalancer 
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080  


macbookair@Macbooks-MacBook-Air kubernetes % kubectl apply -f=users-service.yaml

then start minikube service users-service

http://127.0.0.1:60905/login
email:"test@test.com"
password:"testers"

in reposne you will get token:abc

//let commit first then start again

Video 230 : multiple container in one Pod
