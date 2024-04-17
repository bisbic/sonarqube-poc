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

## Set configs on project to be scanned
```
cp sonar-project.properties /project/path
```
- Edit sonar-project.properties

## Run SonarScanner 
```
cd /project/path
./unziped-sonar-scanner/bin/sonar-scanner \
  -Dsonar.projectKey=<project-key> \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://localhost:9001 \
  -Dsonar.login=<project-login>
```
