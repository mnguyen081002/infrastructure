# infrastructure

## Requirements

##### 1. Build docker image per service

Go to the service directory and run: `docker build -t <image-name> .`

<i>Dont forget run: </i> `eval $(minikube docker-env)` <i>before build image</i>

##### 2. Create configmap for per service

`kubectl create configmap <service-name>-dev-config --from-file=./config/<service-name>/config.yaml`

<i>Now only for user service:</i>

`kubectl create configmap <service-name>-dev-keys --from-file=./config/keys`

##### 3. Create database service

Create volume for database: `kubectl apply -f postgres_ps.yaml`

Create database: `kubectl apply -f postgres_db.yaml`

##### 4. Create service

`kubectl apply -f <service_name>.yaml`
