## Author: Quan NGUYEN
## CFA Insta, 06/05/2022
## kubernetes-evaluation


## Commands: 
### Create pods and services
### Database redis:
```bash
cd ./redis
```
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
```bash
docker build -t redis-react .
```
```bash
docker tag 51c284fcc1dc artemiszz\redis_react:firsttry
```
```bash
docker push artemiszz/redis_react:firsttry
```
```bash
kubectl create -f reds-react-deployement.yaml
```
```bash
kubectl create -f redis-react-service.yaml
```

### Réponses
- Pour multiplier des pods: changer le replicas