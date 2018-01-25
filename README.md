# travis-encrypt-sh

[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

Pure-`bash` script to [encrypt values](https://docs.travis-ci.com/user/encryption-keys/)
for use in [Travis-CI](https://travis-ci.org) build scripts.

Requires `curl`, GNU `sed` and `grep`, and `openssl rsautl` command-line utilities.
(Plus `git` for "magical" autodetection of the correct user and repository from the remote.)

## Installation and usage

```sh
$ curl https://raw.githubusercontent.com/dlenski/travis-encrypt-sh/HEAD/travis-encrypt > ~/bin/travis-encrypt
$ chmod +x !$
$ travis-encrypt
usage:  travis-encrypt [user] [repository] [value to encrypt]

  e.g.: travis-encrypt 'P@ssw0rd' (only inside a git repo)
    or  travis-encrypt jsmith MyRepo 'VAR="s3cret"'
    or  travis-encrypt jsmith MyRepo 'P@ssw0rd'
```

## Inspired by…

[My frustrations here](https://github.com/travis-ci/travis-ci/issues/2982#issuecomment-358873469)
