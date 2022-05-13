# k3d (K3s in Docker)

More info about k3d: <https://github.com/k3d-io/k3d>
More info about K3s: <https://github.com/k3s-io/k3s>

k3d video tutorial: <https://www.youtube.com/watch?v=mCesuGk-Fks>

## Create k3d cluster using config files

More info: <https://github.com/k3d-io/k3d/blob/main/docs/usage/configfile.md>

### Create cluster init config

```sh
k3d config init
```

### Create cluster from config

```sh
# With Traefik ingress controller
k3d cluster create --config traefik/config.yaml

# With Nginx ingress controller
# 1. Go to `nginx/config.yaml` file and update absolute path to `helm-ingress-nginx.yaml` file.
# 2. Create cluster:
k3d cluster create --config nginx/config.yaml
```

### Test cluster, run Nginx web

```sh
# With Traefik ingress controller
kubectl apply --filename traefik/web.yaml

# With Nginx ingress controller
kubectl apply --filename nginx/web.yaml
```

Go to <http://localhost:8081/k3d>

## Delete k3d cluster

```sh
k3d cluster list
k3d cluster delete my-cluster
```
