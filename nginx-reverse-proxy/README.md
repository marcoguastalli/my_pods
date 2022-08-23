# nginx reverse proxy
Accessing a remote minikube from a local computer

You can’t access minikube remotely because it’s only accessible locally.
For this reason, you need to deploy an `nginx reverse proxy` next to minikube that will allow receiving requests from remote clients then forward them to kube-apiserver.


## Inspiring Links
https://faun.pub/accessing-a-remote-minikube-from-a-local-computer-fd6180dd66dd


## ~/.kube/config
a bit of documentation about the file:

### certificate-authority
Provides an API, which lets you provision TLS certificates signed by a Certificate Authority (CA) that you control.
These CA and certificates can be used by your workloads to establish trust.

### server
It’s an address of the Kubernetes API server which validates and configures data for the api objects which include pods,services, replicationcontrollers, and others.

### client-certificate
Kubernetes/minikube requires PKI certificates for authentication over TLS.

### client-key
A key matching the client certificate.


## htpasswd command
https://httpd.apache.org/docs/current/programs/htpasswd.html

### syntax
htpasswd -c /etc/nginx/.htpasswd `user`