# Concourse Meta-Pipeline

A pattern to implements a meta-pipeline that dynamically updates a pipeline
whenever the git source of the pipeline changes.

This removes the need to manually update the pipeline on the command line after
the initial load of the meta-pipeline.

It uses the Concourse pipeline resource:

[Concourse pipeline resource link](https://github.com/concourse/concourse-pipeline-resource)

The files are:

`meta-pipeline.yml`   - The meta-pipeline that defines the pipeline to be run.
`pipelines.yml`       - The pipeline definition that is applied by the Concourse pipeline resource dynamically..
`pipeline.yml`        - A simple hello-world pipeline to run (ie the actual pipeline).

Note that the `pipeline.yml` file could be in a separate repository, with some
minor adjustments to the code. It is in one repository here for simplicity.

## Usage

To do the initial loading of the pipeline:

```
fly -t yourtarget set-pipeline -c meta-pipeline.yml -p meta-pipeline
```

To delete it:

```
fly -t yourtarget destroy-pipeline -p meta-pipeline
```
