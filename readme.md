## Author: Quan NGUYEN
## CFA Insta, 06/05/2022
## kubernetes-evaluation


## Commands: 
### Create pods and services
### Database redis:
```bash
cd ./redis
```
- Pour le déployment Kubernestes:
```bash
kubectl create -f Qredis-deployement.yaml
```
```bash
kubectl create -f redis-service.yaml
```

### API
```bash
cd ./node-redis
```
- Pour le déployment Kubernestes:
```bash
kubectl create -f node-redis-deployement.yaml
```
```bash
kubectl create -f node-redis-service.yaml
```

### Frontend
```bash
cd ./redis-react
```
- Pour build image Docker : 
```bash
docker build -t redis-react .
```
- Pour tag avan push à DockerHub : 
```bash
docker tag 51c284fcc1dc artemiszz\redis_react:firsttry
```
- Pour push à DockerHub : 
```bash
docker push artemiszz/redis_react:firsttry
```
- Pour le déployment Kubernestes:
```bash
kubectl create -f reds-react-deployement.yaml
```
```bash
kubectl create -f redis-react-service.yaml
```

### Réponses
- Pour multiplier des pods: changer le replicas
