# wordpress-alpine-php-soap
Based on [Azure/app-service-quickstart-docker-images/wordpress-alpine-php/0.9](https://github.com/Azure/app-service-quickstart-docker-images/tree/master/wordpress-alpine-php/0.9) modified only to include SOAP


## Modified files

### [local_bin/entrypoint.sh](https://github.com/harupandi/wordpress-alpine-php-soap/blob/master/local_bin/entrypoint.sh)
Added the following before calling supervisord.conf, specifically in line 211.

```
apk update
apk add libxml2 libxml2-dev
docker-php-ext-install soap
```

## Build

> Docker client must be installed before running these steps. You can follow their [documentation](https://docs.docker.com/engine/install/).

1. Clone the repository locally
2. Navigate to the directory where it's cloned
3. Run the following command
```docker build -t <image:tag> -f Dockerfile .```

4. After building locally, you can follow the steps to push to [Azure Container Registry](https://docs.microsoft.com/en-us/azure/app-service/tutorial-custom-container?pivots=container-linux#push-the-image-to-azure-container-registry) or [Dockerhub](https://docs.docker.com/docker-hub/repos/)

5. Modify the App Service's image to use your newly created image:tag.

For further configuration and details please visit the [original](https://github.com/Azure/app-service-quickstart-docker-images/blob/master/wordpress-alpine-php/0.9/README.md) repository.
