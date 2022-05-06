# Examen

## Prérequis

Récupérer le fichier kubeconfig.yml

```SH
export KUBECONFIG=<absolute-path-to>/kubeconfig.yml
```

Vous allez utiliser un cluster distant, il ne faut donc pas utiliser de commandes commençant par `minikube`.

## Tâches

Pour chacun de vos déploiements, pods, services (ou autres), veuillez ajouter votre nom (ou un identifiant que vous m'envoyez par slack) pour permettre d'identifier votre travail.

C'est également important pour les `labels selector` pour éviter les collisions entre le travail de deux élèves.
(un service qui cible des pods de deux personnes).

### Déploiement

Créer 2 deploiements (toutes les images sont fournis) :

- redis (une base https://redis.io/)
- cloud.canister.io:5000/arhturescriou/node-redis (un serveur que j'ai codé)

Cette image est privé il faut donc ajouter l'utilisation du secret pour l'utiliser :

```yaml
spec:
  imagePullSecrets:
    - name: regcred
```

Le serveur (node-redis) nécessite des variables d'environment pour fonctionner

```yaml
env:
  - name: PORT
    value: <port>
  - name: REDIS_URL
    value: redis://<address-of-base>
```

### Service

Créer un service pour communiquer avec le serveur (node-redis) depuis l'extérieur.

### Pods

Un fois qu'un serveur fonctionne augmentez le nombre de pods (node-redis), entre 3 et 5. Et vérifier que cela fonctionne toujours.

## Rendu

Veuillez regrouper tous vos fichiers yaml de déploiement (et ou commande lancées en bash) dans un repository git muni d'un readme.md.

Pousser le repository en ligne (github, gitlab etc).
Et m'envoyer le lien sur slack (cela peut être fait en debut d'examen, je regarderai la dernière version poussé)

## Commandes utiles

Visualiser les ressources déployées

```bash
kubectl get pods
kubectl get services
kubectl get deployments
```

Récupérer les log d'un pod

```bash
kubectl logs <pod-id>
```

Utiliser un fichier yaml, dans votre cas l'image docker ne devrais pas changer donc il est possible de seulement apply le yaml une fois créé

Pensez à nommer votre yaml avec votre nom (et pas juste pod.yaml, pour éviter les collisions)

```bash
kubectl create -f file.yaml
kubectl delete -f file.yaml
kubectl apply -f file.yaml
```
