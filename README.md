# deploy-scripts

Simple way deploy startup.

## Usage

Move files in your repo:

-   .github/workflows/deploy.yml
-   docker-compose.yml

Setup github secrets (envs):

-   `SSH_PRIVATE_KEY` ssh key for entering to server
-   `HOST` docker registry host
-   `USERNAME` ssh username
-   `APP_NAME` folder on remote host
-   `PROJECT_NAME` project name

Change in `docker-compose.yml` line `project/app` and other stuff on yours

Image will be name by `PROJECT_NAME/APP_NAME`, full tagname: `HOST:5000/PROJECT_NAME/APP_NAME`

## How it's work

When some change pushed in repo, github actions run `deploy.yml` script, which do:

1. Build docker image
2. Pushing image to to docker registry (how to run [registry]](https://github.com/fastup-kit/registry))
3. Entering to host
4. Copy docker-compose.yml from repo (can be rewrite by k8s config)
5. Pulling image from registry
6. Starting docker container
7. ...
8. PROFIT
