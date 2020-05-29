# CI/CD sample for SPPP projects (classic SharePoint)

> Azure DevOps continues integration sample

The sample shows a basic pipeline for build and publishing Front-End projects' assets to a SharePoint environment.

## What's SPPP

Yeoman generator for SharePoint client-side applications. [See more](https://github.com/koltyakov/generator-sppp).

## CI/CD Pipeline

[Check pipeline](./azure-pipelines.yml). It contains some comments.

The sample shows the simplest git-flow pipeline:

- commit to `dev` branch: run build & tests (CI pipeline)
- commit to `master` branch: do CI pipeline case plus run assets publishing to SharePoint environment(s)

The pipeline is job-based with a separation to CI and CD part.

CD demonstrates multi-environment deployment bound via matrix strategy.

Each matrix element represents an environment, every environment has separate authentication bindings via `private.json` variable containing multiline JSON, the same as used during local development.

Values like `$(ci.sp.siteurl-env1)` are environment variables. `$(...)` is the syntax to wrap a variable.

## Configuring pipeline in DevOps portal

1. Modify the matrix to represent environments
2. Create new pipeline in Azure DevOps
3. Add the repository as a source
4. Use `yml` as the pipeline definition
5. Create as many environment variables as needed, make sure `Keep this value secret` is toggled on
