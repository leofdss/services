# Services

## Run app in Docker compose

```bash
docker-compose up -d
```
or

```bash
docker compose up -d
```

## Change directory owner

```bash
myUser=$(whoami)
movies=$(realpath ~/Vídeos/movies)
tvseries=$(realpath ~/Vídeos/tvseries)
sudo chown --recursive $myUser $movies
sudo chown --recursive $myUser $tvseries
```
