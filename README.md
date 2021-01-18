# No Secrets Buildpack

![Version](https://img.shields.io/badge/dynamic/json?url=https://cnb-registry-api.herokuapp.com/api/v1/buildpacks/jkutner/no-secrets&label=Version&query=$.latest.version)

This is a [Cloud Native Buildpack](https://buildpack.io) that scans your source code for secrets before building and image. This can prevent leaking secrets into Docker registries or runtime environments where they should not be.

## Usage

You can combine this buildpack with any other buildpack that shares a compatible stack. For example:

```
$ pack build -b jkutner/no-secrets,heroku/nodejs myapp
```

# How it works

The buildpack installs a subset of the [awslabs/git-secrets](https://github.com/awslabs/git-secrets) scripts, and runs it without Git. However, it still uses Git to store patterns (prohibited and allowed), which means `git` is required on the build image.
