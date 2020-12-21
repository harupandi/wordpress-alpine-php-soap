# wordpress-alpine-php
Based on [Azure/app-service-quickstart-docker-images/wordpress-alpine-php/0.9](https://github.com/Azure/app-service-quickstart-docker-images/tree/master/wordpress-alpine-php/0.9) modified only to include SOAP


## Modified files

### entrypoint.sh
Added the following before calling supervisord.conf, specifically in line 211.

```
apk update
apk add libxml2 libxml2-dev
docker-php-ext-install soap
```

For further configuration and details please visit the [original](https://github.com/Azure/app-service-quickstart-docker-images/blob/master/wordpress-alpine-php/0.9/README.md) repository.

