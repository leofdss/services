# media-server

## Microk8s

```bash
sudo snap install microk8s --classic
```

```bash
sudo usermod -a -G microk8s leo
```

```bash
mkdir ~/.kube
```

```bash
sudo chown -R leo ~/.kube
```

> Reboot system

```bash
microk8s enable dns dashboard
```

```bash
microk8s enable hostpath-storage
```

## Run app

```bash
microk8s kubectl apply -f ./volumes/movies-volume.yaml
```

```bash
microk8s kubectl apply -f ./volumes/tvseries-volume.yaml
```

```bash
microk8s kubectl apply -f ./volumes/jellyfin-library-volume.yaml
```

```bash
microk8s kubectl apply -f ./apps/jellyfin-deployment.yaml
```

```bash
microk8s kubectl apply -f ./services/jellyfin-service.yaml
```
