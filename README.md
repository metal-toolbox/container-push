# container-push
A re-usable GitHub workflow that will push a container to GHCR following best practices

## Context

This defines a re-usable workflow that provides best practices for push a container image to the GitHub Container Registry. e.g. this will sign the container and generate provenance information from the build.

## Usage

```yaml
name: Release
on:
  push:
    tags:
      - v**

jobs:
  # Push version being released... e.g. v0.1.0
  container-push-version:
    uses: metal-toolbox/container-push/.github/workflows/container-push.yml@main
    with:
      name: my-container
      tag: ${GITHUB_REF_NAME}
      dockerfile_path: path/to/Dockerfile

  # Push to latest
  container-push-latest:
    uses: metal-toolbox/container-push/.github/workflows/container-push.yml@main
    with:
      name: my-container
      tag: latest
      dockerfile_path: path/to/Dockerfile
```