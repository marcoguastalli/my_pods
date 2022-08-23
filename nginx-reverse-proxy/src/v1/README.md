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