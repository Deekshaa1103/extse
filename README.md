Nagios
step 1:
open docker
step 2:
in powershell 
docker pull jasonrivers/nagios:latest
docker run --name demo -p 8888:80 jasonrivers/nagios:latest
step 3:
open port 8888
user: nagiosadmin
password: nagios
step 4:
powershell
docker ps
docker rm demo
docker images
docker rmi jasonrivers/nagios




kubernet
step 1:
in cmd -- minikube start
step 2:
in cmd -- kubectl create deployment mynginx --image-nginx
step 3:
in cmd -- kubectl get deployments
in cmd -- kubectl expose deployment mynginx --type=NodePort --port=80 --target-port=80
in cmd -- kubectl scale deployment mynginx --replicas=4
in cmd -- kubectl get deployments
in cmd -- kubectl get pods
in cmd -- kubectl port-forward svc/mynginx 8081:80
step 4:
localhost:8081 -- nginx opens
step 5:
in cmd -- minikube dashboard
step 6:
in cmd -- kubectl delete deployment mynginx
in cmd -- kubectl delete service mynginx
in cmd -- minikube stop




docker-compose
version: '3.8'  # Docker Compose file format version

services:
  wordpress:  # WordPress service
    image: wordpress:latest
    ports:
      - "8080:80"  # Map port 80 of the container to port 8080 of the host
    environment:
      WORDPRESS_DB_HOST: db:3306  # Database host
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
    depends_on:
      - db  # Ensures the db service starts first

  db:  # MySQL service
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress

cmd
docker-compose up --build
docker ps
docker-compose down






