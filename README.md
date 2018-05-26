0. Build WEBAPP container
`docker build -t webapp server/`

1. Initialize stack
`docker stack deploy --compose-file docker-compose.yml webapp`

* Troubleshooting
`docker network create webapp-network`
`docker run --net "webapp-network" -d -p 6379:6379 --name redis redis:alpine`
`docker run --net "webapp-network" --env REDIS_HOST=redis -p 3000:3000 webapp`

* Docker service 
- Initialize stack: `docker stack deploy --compose-file docker-compose.yml webapp`
- Remove stack: `docker stack rm <NAME>`	

