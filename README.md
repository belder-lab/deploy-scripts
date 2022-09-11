# deploy-scripts

Simple way deploy startup.

## Usage

Move files in your repo:

-   .github/workflows/deploy.yml
-   docker-compose.yml

Setup github secrets (envs):

-   `SSH_PRIVATE_KEY` ssh key for entering to server
-   `HOST` docker registry and application host
-   `USERNAME` ssh username
-   `APP_NAME` folder on remote host
-   `PROJECT_NAME` project name
-   `REGISTRY_USERNAME` username for registry
-   `REGISTRY_TOKEN` token for registry

Change in `docker-compose.yml` line `project/app` and other stuff on yours

Image will be name by `PROJECT_NAME/APP_NAME`, full tagname: `HOST:5000/PROJECT_NAME/APP_NAME`

## How it's work

When some change pushed in repo, github actions run `deploy.yml` script, which do:

1. Login to docker registry (how to run [registry]](https://github.com/fastup-kit/registry))
2. Build docker image
3. Pushing image to to docker registry
4. Entering to host
5. Copy docker-compose.yml from repo (can be rewrite by k8s config)
6. Pulling image from registry
7. Starting docker container
8. ...
9. PROFIT
