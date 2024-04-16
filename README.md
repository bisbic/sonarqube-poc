# SonarQube

## Host setup for Elasticsearch
```
# To be run in the same shell as the following docker commands
sudo sysctl -w vm.max_map_count=262144
sudo sysctl -w fs.file-max=65536
ulimit -n 65536
ulimit -u 4096
```

## Launch SonarQube with docker compose
`docker compose up -d`

## Open on (http://localhost:9001)[http://localhost:9001]
Login: admin
Password: admin

## Project setup
- Setup type: Manually
- Project display name: SonarQubeDemo
- Project key: SonarQubeDemo
- Main branch name: master
- Location: Locally
- Setup .env using the environment variables values returned by the project setup
- Load environment:
```
source .env
```

## Run SonarScanner 
```
docker run \
    --rm \
    -e SONAR_HOST_URL="${SONAR_HOST_URL}" \
    -e SONAR_SCANNER_OPTS="-Dsonar.projectKey=${PROJECT_KEY}" \
    -e SONAR_LOGIN="${SONAR_LOGIN}" \
    -v "${YOUR_REPO}:/usr/src" \
    sonarsource/sonar-scanner-cli
```
