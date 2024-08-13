# CI-PIPELINE-GITHUB
## Description
This repository contains a GitHub Actions pipeline that create Docker image to public Docker Hub.

## Developement
### Local Deployment
To deploy the pipeline locally, you need to have Docker installed. Then, you can run the following command:

```bash
docker compose up
```

This triggers two services:
- `pytest` service: runs the tests in the `app` folder with `test_*.py`. (on success webserver is started)
- `web` service: runs the webserver locally on `http://localhost:28000`.

### CI Pipeline

This triggers the pipeline on a push event on the master branch. (code is in `.github/workflows/main.yml`)

The pipeline consists of the following steps:
- Checkout the code
- Build the Docker image
- Run the tests
- Push the Docker image to Docker Hub

#### Secrets
- `DOCKER_USERNAME`: Docker Hub username
- `DOCKER_TOKEN`: Docker Hub token

## Webser
### Endpoints
```curl
GET http://localhost:28000/
```

```json
200 OK
{
    "message": "Hello World"
}
```