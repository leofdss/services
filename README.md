# Services

## Docker and Docker Compose - Ubuntu and Fedora

```bash
bash <(wget -qO- https://raw.githubusercontent.com/leofdss/setup-desktop/main/docker/install.sh)
```

> Reboot system

## Run app in Docker compose

```bash
docker-compose up -d
```

## Change directory owner

```bash
myUser=$(whoami)
movies=$(realpath ~/Vídeos/movies)
tvseries=$(realpath ~/Vídeos/tvseries)
sudo chown --recursive $myUser $movies
sudo chown --recursive $myUser $tvseries
```
