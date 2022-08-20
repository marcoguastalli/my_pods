### build
cd ~/dev/repository/git/my_pods/mongodb/src/v1

### first setup
echo -n 'adminuser' | base64

### deploy to remote host
scp -i ~/.ssh/id_rsa_nhe ~/dev/repository/git/my_pods/mongodb/src/v1/mongodb-secrets.yaml marco.guastalli@minikube:/home/marco.guastalli/my_pods/mongodb-secrets.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-secrets.yaml marco.guastalli@minikube:/opt/my_pods/mongodb/mongodb-secrets.yaml

### deploy on remote host
login as search user
kubectl apply -f /opt/my_pods/mongodb/mongodb-secrets.yaml
  secret/mongo-creds created

## play
