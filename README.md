# deploy-scripts

Simple way deploy startup.

## Usage

Setup github secrets (envs):

-   `SSH_PRIVATE_KEY` ssh key for entering to server
-   `HOST` docker registry host
-   `USERNAME` ssh username
-   `APP_NAME` folder on remote host
-   `PROJECT_NAME` project name

Change in docker-compose `project/app` and other stuff on yours

Image will be name by `PROJECT_NAME/APP_NAME`, full tagname: `HOST:5000/PROJECT_NAME/APP_NAME`

## CD Steps

1. Build
2. Push to to docker registry (how to run [registry]](https://github.com/fastup-kit/registry))
3. Entering to host
4. Copy docker-compose.yml from repo (can be rewrited by k8s config)
5. Pulling image from registry
6. Starting docker container
7. ...
8. PROFIT
