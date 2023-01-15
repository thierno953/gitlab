# Build-and-Push-Docker-Image-to-GitLab-Container-Registry

### GitLab CI CD pipeline to push the docker image to Container registry

#### Authenticate with the Container Register

- CI_REGISTRY_USER CI/CD variable

```bash
docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
```

- CI job token

```bash
docker login -u $CI_JOB_USER -p $CI_JOB_TOKEN $CI_REGISTRY
```

- Personal access token

```bash
docker login -u <username> -p <access_token> $CI_REGISTRY
```
