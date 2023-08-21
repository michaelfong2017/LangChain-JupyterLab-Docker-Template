# LangChain-JupyterLab-Docker-Template

This project is an open-source endeavor that serves as a comprehensive template for initiating a JupyterLab sandbox dedicated to LangChain development. Its primary objective is to provide a robust foundation and framework for developers looking to kickstart their LangChain-related projects within a JupyterLab environment.

A Dockerfile is provided to start an isolated environment for development.

Environment specification:

- Ubuntu 22.04.
- Miniforge3, which is a minimal distribution of the Conda package manager. conda-forge will be used as the default channel for pulling packages, conda-libmamba-solver is used as the default dependency solver for Conda.
- JupyterLab Server is automatically started for development. Port 8888 is exposed.

## Instruction for development

1. Navigate to the project root directory.

2. Use Docker Compose to run all necessary services (in detach mode).

```bash
docker-compose up -d
```

- Note that the directory `<PROJECT_ROOT>/sandbox` is mounted to the `/sandbox` directory inside the docker container. Therefore, any updates inside the docker container are equivalent to the updates in your host machine. You can commit the changes to git. When others pull your changes, their files inside docker container will also be updated.
