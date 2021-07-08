1) Build docker image for app
docker build -t vladyslavstepanenko1/helloworld-app -f ./helloworld-app/Dockerfile ./helloworld-app

2) Push image to Docker Hub
docker push vladyslavstepanenko1/helloworld-app

3) Create minikube cluster and specify virtualbox as driver
minikube start --driver=virtualbox

4) Create deployment for helloworld-app
kubectl apply -f helloworld-app-deployment.yaml

5) Scale application up to 2 replicas
kubectl scale deployment helloworld-app-deployment --replicas=2

6) Create service (ClusterIP) for helloworld-app
kubectl apply -f helloworld-app-service.yaml

7) Install nginx ingress controller
minikube addons enable ingress

8) Ensure that nginx ingress pod up & running
kubectl get pods -n ingress-nginx -l app.kubernetes.io/name=ingress-nginx

9) Create ingress controller which routes traffic from helloworld-app.com ---> helloworld-app-service:8000