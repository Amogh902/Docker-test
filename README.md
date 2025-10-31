## Q1 --> C The container exited because no foreground process was running
## Q2 --> B The second command will fail due to port conflict
## Q3 --> A Exited
## Q4 --> B  --rm
## Q5 --> A  Yes
## Q6 --> D  ENTRYPOINT keeps its command fixed, while CMD provides default arguments


# Dockerfile

## Q1 --> C WORKDIR
## Q2 --> A yes
## Q3 --> C FROM nginx RUN echo "Deployed"
## Q4 --> B Prevent files from being copied during the build context upload
## Q5 --> C Only the last one takes effect
## Q6 --> B 2 

# Docker networks

## Q1 --> B bridge, none, host
## Q2 --> c overlay
## Q3 --> A yes
## Q4 --> A bridge
## Q5 --> c docker network connect
## Q6 --> A By container name and port 5000 

# Docker-compose 

## Q1 --> A The name of the current directory
## Q2 --> B Controls startup order only
## Q3 --> A Docker Compose ignores removed services
## Q4 --> C docker-compose ps
## Q5 --> C  Uses the bridge network
## Q6 --> C Overwritten each time

# Docker volumes

## Q1 --> A Named volume
## Q2 --> A yes
## Q3 --> C Bind mount can map to any host path, named volume is managed by Docker
## Q4 --> B docker rm volume
## Q5 --> B Remains on the host
## Q6 --> B myvol will appear immediately


# Practical Task 

### Create Two Custom Bridge Networks

```bash
docker network create --driver bridge --subnet 172.18.0.0/16 net1
docker network create --driver bridge --subnet 172.19.0.0/16 net2
```
### Run Containers in Separate Networks

```bash
docker run -d --name c1 --network net1 nginx 
docker run -d --name c2 --network net2 nginx
```
### Install `ping` Command

```bash
docker exec -it c1 bash
apt update && apt install -y iputils-ping
exit
```

### Connect One Container to Both Networks

```bash
docker network connect net2 c1
```
### Verify Communication

```bash
docker exec c1 ping c2
```
