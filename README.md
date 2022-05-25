# Dagster Sandbox Example (Experimental)

Sandbox Deployments allow you to rapidly prototype changes to Dagster jobs. You can use your local development environment to make changes and you can run them as actual Dagster jobs in your cloud environment.


This repository has an example Docker image that you can use to launch your first Dagster Sandbox.

## Getting started

1. Complete the [prerequisites for running a Sandbox Deployment](https://docs.dagster.cloud/guides/sandbox-deployments#prerequisites).

2. Clone this repository:

  ```sh
  git clone git@github.com:dagster-io/dagster-sandbox-example.git
  ```

3. Change directory into the repository's directory:

  ```sh
  cd dagster-sandbox-example
  ```

4. Add the `sandbox-example` code location to your Sandbox Deployment:

  ```yaml
  location_name: sandbox-example
  image: dagster/dagster-sandbox-example:latest
  code_source:
    package_name: example
  ```

5. Begin syncing your local directory with your remote code location:

  ```sh
  dagster-cloud sandbox sync
  ```

You can now modify the `example` package and see the code change in real-time on Dagster Cloud. Try adding a new op to `foo_job` in `repo.py` and launching a run!

## Next steps

You can turn your existing image into a Dagster Sandbox compatible image by building from our [base image](https://hub.docker.com/repository/docker/dagster/dagster-cloud-base). For example:

```dockerfile
FROM dagster/dagster-cloud-base:latest
COPY my-dagster-code .
RUN pip install ./my-dagster-code
```
