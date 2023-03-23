# docker-images-ci

Repository with Dockerfile for create image for CI (gitlab-ci ; github actions etc...)

## Quality Analysis

Dockerfile is based on work of Jakub Zalas (https://github.com/jakzal/phpqa)

Tools available : https://github.com/jakzal/phpqa#available-tools

In order to build this image, use DOCKER_BUILDKIT=1 environment variable :
```
cd quality-analysis/
DOCKER_BUILDKIT=1 docker build .
```

## Tests

Dockerfile create an image with php and necessary things for execute phpunit (https://github.com/sebastianbergmann/phpunit) et Panther tests (https://github.com/symfony/panther).
