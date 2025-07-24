## Clear-env buildpack behavior

```
$ echo "clear-env = true" >> buildpack.toml
$ pack build inline-bp-test --clear-cache --path . --buildpack . --env HELLO=world | grep HELLO -A5 -B5
[builder]
=== CNB_PLATFORM_DIR/env/ Contents ===
[builder] Directory exists: /platform/env
[builder] total 12
[builder] drwxr-xr-x 1 root root 4096 Jul 24 21:22 .
[builder] drwxr-xr-x 1 root root 4096 Jul 24 21:22 ..
[builder] -rw-r--r-- 1 root root    5 Jan  1  1980 HELLO
[builder]
[builder] === Contents of each file in CNB_PLATFORM_DIR/env/ ===
[builder] --- File: HELLO ---
[builder] world
[builder] === Environment Debug Buildpack Completed ===
===> EXPORTING
[exporter] Reusing layer 'buildpacksio/lifecycle:launch.sbom'
[exporter] Reused 1/1 app layer(s)
```

```
$ echo "clear-env = true" >> buildpack.toml
$ pack build inline-bp-test --clear-cache --path . --buildpack . --env HELLO=world | grep HELLO -A5 -B5
[builder]
[builder] === CNB_PLATFORM_DIR/env/ Contents ===
[builder] Directory exists: /platform/env
[builder] total 12
[builder] drwxr-xr-x 1 root root 4096 Jul 24 21:22 .
[builder] drwxr-xr-x 1 root root 4096 Jul 24 21:22 ..
[builder] -rw-r--r-- 1 root root    5 Jan  1  1980 HELLO
[builder]
[builder] === Contents of each file in CNB_PLATFORM_DIR/env/ ===
[builder] --- File: HELLO ---
[builder] world
[builder] === Environment Debug Buildpack Completed ===
===> EXPORTING
[exporter] Reusing layer 'buildpacksio/lifecycle:launch.sbom'
[exporter] Reused 1/1 app layer(s)
```

```
$ echo "clear-env = false" >> buildpack.toml
$ pack build inline-bp-test --clear-cache --path ./test-app --buildpack . --env HELLO=world | grep HELLO -A5 -B5
[builder] CNB_STACK_ID=heroku-24
[builder] CNB_TARGET_ARCH=arm64
[builder] CNB_TARGET_DISTRO_NAME=ubuntu
[builder] CNB_TARGET_DISTRO_VERSION=24.04
[builder] CNB_TARGET_OS=linux
[builder] HELLO=world
[builder] HOME=/home/heroku
[builder] HOSTNAME=c7e391ce428a
[builder] PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
[builder] PWD=/workspace
[builder] SHLVL=1
--
[builder] === CNB_PLATFORM_DIR/env/ Contents ===
[builder] Directory exists: /platform/env
[builder] total 12
[builder] drwxr-xr-x 1 root root 4096 Jul 24 21:22 .
[builder] drwxr-xr-x 1 root root 4096 Jul 24 21:22 ..
[builder] -rw-r--r-- 1 root root    5 Jan  1  1980 HELLO
[builder]
[builder] === Contents of each file in CNB_PLATFORM_DIR/env/ ===
[builder] --- File: HELLO ---
[builder] world
[builder] === Environment Debug Buildpack Completed ===
===> EXPORTING
[exporter] Reusing layer 'buildpacksio/lifecycle:launch.sbom'
[exporter] Reused 1/1 app layer(s)
```
