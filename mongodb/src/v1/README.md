### build
cd ~/dev/repository/git/my_pods/mongodb/src/v1

### first setup
echo -n 'adminuser' | base64

### deploy
scp -i ~/.ssh/id_rsa_nhe ~/dev/repository/git/my_pods/mongodb/src/v1/mongodb-secrets.yaml marco.guastalli@pf-cloud-minikube.nhe.netcentric.biz:/home/marco.guastalli/mongodb-secrets.yaml
scp -i ~/.ssh/id_rsa_nhe mongodb-secrets.yaml marco.guastalli@pf-cloud-minikube.nhe.netcentric.biz:/home/marco.guastalli/mongodb-secrets.yaml

### run

## play
