# automation project based on Terraform, github actions, docker and aws 
This project leverages automation for building docker images , pushing it to dockerHub and running integration test.


### technologies and services used in this project

- GitHub Actions - CI/CD pipeline for deployment automation.
- Docker - Application containerization.
- Docker Compose - Orchestration of containers in local development environments.


### Running Project Locally

This project runs using Docker. 

```sh
docker compose -f docker-compose.local.yml up 
```

 Browse the project at [http://127.0.0.1:3000]

### Running Tests Locally


```sh
docker compose -f docker-compose.testinglocal.yml up --abort-on-container-exit --remove-orphans

docker compose -f docker-compose.testinglocal.yml down --volumes
```


# Running CI/CD



### GitHub Actions Variables

This section lists the GitHub Actions variables which need to be configured on the GitHub project.

Variables:
- `DOCKERHUB_USER`: Username for [Docker Hub](https://hub.docker.com/) for avoiding Docker Pull rate limit issues.
- `PORT` golang api port 
- `FRONT_URL` frontend container name 
- `BASEURL` api contanier name 
- `DB_HOST` psql container name 
- `DB_PORT` psql port
- `DB_USER` psql username 
- `DB_PASSWORD` psql password
- `DB_DBNAME` psql database name 
- `AUTH0_AUDIENCE` your auth0 audience 
- `AUTH0_CLIENT_ID`your auth0 client Id
- `AUTH0_EMAIL` your auth0 email 


Secrets:


- `DOCKERHUB_TOKEN`: Token created in `DOCKERHUB_USER` in [Docker Hub](https://hub.docker.com/).
- `AUTH0_PASSWORD` your auth0 password  
- `AUTH0_DIET_ENDPOINT` your auth0 endpoint  
- `AUTH0_DOMAIN` your auth0 domain 

# To trigger the CI/CD process, you simply need to merge a Pull Request into the main or prod branch, or commit directly to main/prod.


#### Section Notes and Resources
This project contains golang api and nuxt3 frontend borrowed from my friend  (https://github.com/1ChaLLengeR1/diet_project_frontend_nuxt3).
