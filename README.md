# Publish to JSR

This workflow can publish a pacakge to the
[JavaScript Registory](https://jsr.io/) (JSR) when a git tag is added.

This enables for a separate timing for committing the configuration file
(`jsr.json` or `deno.json`) and publishing a package.

## Limitations

The `version` field in the configuration file must match the end of the created
tag. If it doesn't match, no publishing a package.

||version field|git tag|
|---|:---:|---|
|good|0.1.0|0.1.0, v0.1.0, release-0.1.0|
|bad|0.1.0|0.1.1, 0.1.0-2024-05-11, 0.1.0-rc1|

## Setup the workflow file

### Modify the workiflow trigger

Change it to suit your project. The default setting is to run the workflow when
any tag is pushed.

```yaml
on:
  push:
    tags:
      - '*'
```

### Set your configuration file name

By default, the name of the configuration file is `jsr.json`.

```yaml
env:
  CONFIG_FILE: jsr.json
```

### Copy the workflow file to the `.github/workflows/` folder and commit it

That's all done.

## How to use

1. Set the version you want to publish in the version field, and commit the
   configuration file and push to the repository to the github.com server.

2. Add a tag and push it to the remote repository on the github.com server,
   OR, create a release with a new tag on the github.com website.

## License

MIT License
