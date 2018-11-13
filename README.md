# docker-compose LAMP setup
This repository contains the bare-bones setup for a LAMP stack with docker-compose. The php-apache container provides composer for project installation and should have all necessary php extensions for using the most common frameworks.

Make sure to use the `www-data` user if you install your project via composer, e.g.:

```
docker exec -it --user www-data container_www_1 bash
```