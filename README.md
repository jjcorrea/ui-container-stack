# ui-container-stack

### build webapp container
- `docker build -t webapp server/`
### initialize stack
- `docker stack deploy --compose-file docker-compose.yml webapp`
#### remove stack
- `docker stack rm webapp`	
#### service scale
- `docker service scale webapp_app=10`
### troubleshooting
- `docker network create webapp-network`
- `docker run --net "webapp-network" -d -p 6379:6379 --name redis redis:alpine`
- `docker run --net "webapp-network" --env REDIS_HOST=redis -p 3000:3000 webapp`
### validated
- :white_check_mark: sticky session based on source affinity
- :white_check_mark: reconnection after scale down
