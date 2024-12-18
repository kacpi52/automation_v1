# farmacy Api is automation project based on Terraform, github actions, docker and aws 
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

 Browse the project at [http://127.0.0.1:3000]

### Running CI/CD

```

### GitHub Actions Variables

This section lists the GitHub Actions variables which need to be configured on the GitHub project.

Variables:

- `AWS_ACCESS_KEY_ID`: Access key for the CD AWS IAM user that is created by Terraform and output as `cd_user_access_key_id`.
- `AWS_ACCOUNT_ID`: AWS Account ID taken from AWS directly.
- `DOCKERHUB_USER`: Username for [Docker Hub](https://hub.docker.com/) for avoiding Docker Pull rate limit issues.
- `ECR_REPO_APP`: URL for the Docker repo containing the app image output by Terraform as `ecr_repo_app`.
- `ECR_REPO_PROXY`: URL for the Docker repo containing the proxy image output by Terraform as `ecr_repo_proxy`.

Secrets:

- `AWS_SECRET_ACCESS_KEY`: Secret key for `AWS_ACCESS_KEY_ID` set in variables, output by Terraform as `cd_user_access_key_secret`.
- `DOCKERHUB_TOKEN`: Token created in `DOCKERHUB_USER` in [Docker Hub](https://hub.docker.com/).
- `TF_VAR_DB_PASSWORD`: Password for the RDS database (make something up).
- `TF_VAR_DJANGO_SECRET_KEY`: Secret key for the Django app (make something up).


# To trigger the CI/CD process, you simply need to merge a Pull Request into the main or prod branch, or commit directly to main/prod.



#### Section Notes and Resources
This project contains golang api and nuxt3 frontend borrowed from my friend  (https://github.com/1ChaLLengeR1/diet_project_frontend_nuxt3).
