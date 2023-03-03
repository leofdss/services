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
microk8s kubectl apply -f movies-volume.yaml
```

```bash
microk8s kubectl apply -f tvseries-volume.yaml
```

```bash
microk8s kubectl apply -f jellyfin-library-volume.yaml
```

```bash
microk8s kubectl apply -f jellyfin-deployment.yaml
```

```bash
microk8s kubectl apply -f jellyfin-service.yaml
```
