# Publish to JSR

This workflow tiggers a git tag to publish a package to the
[JavaScript Registory](https://jsr.io/) (JSR).

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

If you want to run it when released, configure as follows.

```yaml
on:
  release:
    types: [published]
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

1. Set the version you want to publish in the `version` field, and commit the
   configuration file and push to the repository on the Github site.

2. Trigger the event that you specified.

## License

MIT License
