# nifi-development
 
 Repository for developers to work on Nifi flows locally before sending templates to production

 This docker-compose configuration file uses the NiFi docker image to launch a 2-node NiFi cluster.
The NiFi configuration and repositories are persisted in Docker volumes, so they survive cluster restarts.

The cluster is configured to use the `single-user` provider and authorizer. The default credentials are `admin/supersecret1`. You can change this in the configuration file if needed.

A `nginx` service is also part of the deployment to distribute connections to both NiFi nodes. To connect to the cluster, point your browser to `https://localhost:8443/nifi`.

The temp directory in this repository is bound to the container. You can write output here for testing flows and easy inspection of the final results.

## Starting the cluster

Execute the following command on this directory:

`docker compose up -d`

## Stopping the cluster

Execute the following command on this directory:

`docker compose down`


## Resetting the cluster content

If you want to clear/discard the content of your NiFi cluster so that you can start a fresh one, execute the following commands on this directory:

`docker compose down`
`docker volume rm $(docker volume ls -q --filter "name=nifi-docker-compose"`

