# deploy-video-filter

Deploy a of video-service in FILTER mode (running as dedicated edge-service).

## Slik går du fram for å kjøre dette lokalt eller på en skytjeneste
1. Sette opp virtuell server.
2. Networking: Open up port 8080 for incoming traffic from any * incoming source.

```Shell
sudo apt update

sudo apt install docker-compose eller curl -sSL https://get.docker.com | sh
sudo git clone https://github.com/langrenn-sprint/deploy-video-filter.git
# copy .env
sudo usermod -aG docker $USER #deretter logge ut og inn igjen
# opprette en .env fil med miljøvariable, se under
source .env
docker-compose pull
docker-compose up &
```

## Monitorere logger

Gå til folderen der docker-compose filen ligger og kjør følgende kommando:

```Shell
docker-compose logs -f
```

## Stoppe containere

Følgende kommando stopper alle services:

```Shell
docker-compose stop
docker-compose down
```

## Miljøvariable

Du må sette opp ei .env fil med miljøvariable, som eksemplet. Merk at server referanser må oppdateres dersom andre services ikke kjøres lokalt. Sikre også at containeren har skrivetilgang til LOCAL_PHOTO_DIRECTORY.

```Shell
LOGGING_LEVEL=INFO
ADMIN_USERNAME=admin
ADMIN_PASSWORD=password
EVENTS_HOST_SERVER=localhost
EVENTS_HOST_PORT=8082
PHOTOS_HOST_SERVER=localhost
PHOTOS_HOST_PORT=8092
USERS_HOST_SERVER=localhost
USERS_HOST_PORT=8086
LOCAL_PHOTO_DIRECTORY=/home/github/deploy-video-filter/files
```
