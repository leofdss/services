# Services

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
sudo chown -R $(whoami) ~/.kube
```

> Reboot system

```bash
microk8s enable dns dashboard
```
 
```bash
microk8s enable hostpath-storage
```

## Add-on gpu

> Microk8s Required

```bash
microk8s enable gpu
```

```bash
microk8s kubectl logs -n gpu-operator-resources -lapp=nvidia-operator-validator -c nvidia-operator-validator
```

## Docker and Docker Compose

```bash
sudo apt update && \
sudo apt install docker.io && \
sudo apt install docker-compose
```

```bash
sudo systemctl start docker && \
sudo systemctl enable docker && \
sudo usermod -aG docker $USER
```

> Reboot system

## NVIDIA Container Toolkit

> Docker required

```bash
distribution="ubuntu22.04" \
      && curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
      && curl -s -L https://nvidia.github.io/libnvidia-container/$distribution/libnvidia-container.list | \
            sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
            sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```

```bash
sudo apt update && \
sudo apt install -y nvidia-container-toolkit && \
sudo nvidia-ctk runtime configure --runtime=docker && \
sudo systemctl restart docker && \
sudo docker run --rm --runtime=nvidia --gpus all nvidia/cuda:11.6.2-base-ubuntu20.04 nvidia-smi
```

## Run app in Microk8s

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

## Run app in Docker compose

```bash
docker-compose up -d
```
