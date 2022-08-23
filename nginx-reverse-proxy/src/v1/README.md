# v1
Accessing a remote minikube from a local computer

### build
cd ~/dev/repository/git/my_pods/nginx-reverse-proxy/src/v1

### first setup
As minikube is supposed to be installed in your (not root) `user`, enter there:

##### login and get the minikube ip
ssh minikube
sudo su `user`
cd
minikube ip

##### create nginx folders
sudo mkdir -p /etc/nginx/conf.d/ /etc/nginx/certs

##### edit file /etc/nginx/conf.d/minikube.conf
sudo nano /etc/nginx/conf.d/minikube.conf

##### create .htpasswd file
htpasswd -c /etc/nginx/.htpasswd `user`

##### run a nginx docker container
docker run -d \
--name nginx \
-p 8080:80 \
-v /home/search/.minikube/profiles/minikube/client.key:/etc/nginx/certs/minikube-client.key \
-v /home/search/.minikube/profiles/minikube/client.crt:/etc/nginx/certs/minikube-client.crt \
-v /etc/nginx/conf.d/:/etc/nginx/conf.d \
-v /etc/nginx/.htpasswd:/etc/nginx/.htpasswd \
nginx

##### docker ps
eb2afc266d3c nginx "/docker-entrypoint.…"   5 seconds ago   Up 4 seconds   0.0.0.0:8080->80/tcp, :::8080->80/tcp   nginx

##### curl -I http://localhost:8080
HTTP/1.1 401 Unauthorized
Server: nginx/1.23.1
Date: Tue, 23 Aug 2022 19:16:53 GMT
Content-Type: text/html
Content-Length: 179
Connection: keep-alive
WWW-Authenticate: Basic realm="Administrator’s Area"

