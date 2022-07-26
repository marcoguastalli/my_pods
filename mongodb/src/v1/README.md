### build
cd ~/dev/repository/git/my_pods/mongodb/src/v1

### first setup
echo -n 'adminuser' | base64

### deploy to remote host
scp -i ~/.ssh/id_rsa_nhe ~/dev/repository/git/my_pods/mongodb/src/v1/mongodb-secrets.yaml marco.guastalli@pf-cloud-minikube.nhe.netcentric.biz:/home/marco.guastalli/mongodb-secrets.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-secrets.yaml marco.guastalli@pf-cloud-minikube.nhe.netcentric.biz:/home/marco.guastalli/mongodb-secrets.yaml

### deploy on remote host
login
mv mongodb-secrets.yaml /opt/my_pods/mongodb
kubectl apply -f /opt/my_pods/mongodb/mongodb-secret.yaml

## play
