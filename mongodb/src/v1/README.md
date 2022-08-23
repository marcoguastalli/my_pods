# v1
MongoDB Server and Client PODS

### build
cd ~/dev/repository/git/my_pods/mongodb/src/v1

### first setup
echo -n 'adminuser' | base64

### deploy to remote host
scp -i ~/.ssh/id_rsa_nhe ~/dev/repository/git/my_pods/mongodb/src/v1/mongodb-secrets.yaml marco.guastalli@minikube:/home/marco.guastalli/my_pods/mongodb-secrets.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-secrets.yaml marco.guastalli@minikube:/my_pods/mongodb/mongodb-secrets.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-pvc.yaml marco.guastalli@minikube:/my_pods/mongodb/mongodb-pvc.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-deployment.yaml marco.guastalli@minikube:/my_pods/mongodb/mongodb-deployment.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-nodeport-svc.yaml marco.guastalli@minikube:/my_pods/mongodb/mongodb-nodeport-svc.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-client.yaml marco.guastalli@minikube:/my_pods/mongodb/mongodb-client.yaml

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
kubectl create -f mongodb-nodeport-svc.yaml
        service/mongo-nodeport-svc created
kubectl get services
minikube ip
minikube service --url mongo-nodeport-svc
        http://192.168.49.2:32000
mongo --host <ip> --port <port of nodeport svc> -u adminuser -p password123
mongo --host 192.168.49.2 --port 32000 -u adminuser -p password123

kubectl create -f mongodb-client.yaml
        deployment.apps/mongo-client created
kubectl exec deployment/mongo-client -it -- /bin/bash
        mongo --host 192.168.49.2 --port 32000 -u adminuser -p password123
        show dbs
        use local
        show collections
        db.createCollection("bookmarks")
        db.bookmarks.count()
        db.getCollectionInfos()
        db.bookmarks.find();