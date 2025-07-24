# Inline Buildpack Example

This example demonstrates how to use an inline buildpack to debug environment variables and inspect the `$CNB_PLATFORM_DIR/env/` directory during the build process.

## Repro

Run without env vars:

```
$ pack build inline-bp-test --clear-cache --path .
```

Run with env vars:

```
$ pack build inline-bp-test --clear-cache --path . --env HELLO=world
```

## Demo

```
$ pack --version
0.38.2+git-f1c347c.build-6533
$ pack build inline-bp-test --clear-cache --path . --env HELLO=world
=== Current Environment Variables ===
CNB_BP_PLAN_PATH=/tmp/me_env-debug-866359196/me_env-debug/plan.toml
CNB_BUILDPACK_DIR=/cnb/buildpacks/me_env-debug/0.0.0
CNB_LAYERS_DIR=/layers/me_env-debug
CNB_PLATFORM_DIR=/platform
CNB_STACK_ID=heroku-24
CNB_TARGET_ARCH=arm64
CNB_TARGET_DISTRO_NAME=ubuntu
CNB_TARGET_DISTRO_VERSION=24.04
CNB_TARGET_OS=linux
HELLO=world
HOME=/home/heroku
HOSTNAME=65bd3b5d7e2b
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PWD=/workspace

=== CNB_PLATFORM_DIR/env/ Contents ===
Directory exists: /platform/env
total 12
drwxr-xr-x 1 root root 4096 Jul 24 20:55 .
drwxr-xr-x 1 root root 4096 Jul 24 20:55 ..
-rw-r--r-- 1 root root    5 Jan  1  1980 HELLO

=== Contents of each file in CNB_PLATFORM_DIR/env/ ===
--- File: HELLO ---
world
```

## What the Inline Buildpack Does

The inline buildpack defined in `project.toml` will:

1. **Echo all current environment variables** - Shows all environment variables available during the build process, sorted alphabetically
2. **List contents of `$CNB_PLATFORM_DIR/env/`** - Shows the directory structure and contents of any files in the platform environment directory
3. **Display file contents** - If any files exist in the platform env directory, it will show their contents

## Files

- `project.toml` - Contains the inline buildpack definition

## References

- [Inline Buildpack Documentation](https://buildpacks.io/docs/for-app-developers/how-to/build-inputs/use-inline-buildpacks/)
- [Cloud Native Buildpacks](https://buildpacks.io/)
