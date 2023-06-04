# Services

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

## Run app in Docker compose

```bash
docker-compose up -d
```
