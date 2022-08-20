### build
cd ~/dev/repository/git/my_pods/mongodb/src/v1

### first setup
echo -n 'adminuser' | base64

### deploy to remote host
scp -i ~/.ssh/id_rsa_nhe ~/dev/repository/git/my_pods/mongodb/src/v1/mongodb-secrets.yaml marco.guastalli@minikube:/home/marco.guastalli/my_pods/mongodb-secrets.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-secrets.yaml marco.guastalli@minikube:/my_pods/mongodb/mongodb-secrets.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-pvc.yaml marco.guastalli@minikube:/my_pods/mongodb/mongodb-pvc.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-deployment.yaml marco.guastalli@minikube:/my_pods/mongodb/mongodb-deployment.yaml

### deploy on remote host
login as search user
kubectl apply -f /my_pods/mongodb/mongodb-secrets.yaml
        secret/mongo-creds created
  kubectl get secrets
kubectl create -f mongodb-pvc.yaml
        persistentvolumeclaim/mongo-data unchanged
  kubectl get pvc
kubectl apply -f mongodb-deployment.yaml
        deployment.apps/mongo created
kubectl get deployments



## play
