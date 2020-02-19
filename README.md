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

Let's encrypt a secret value for use in the `.travis.yml` of *this* GitHub repository:

```sh
$ ./travis-encrypt dlenski travis-encrypt-sh 's3cr3t-va1ue' > base64.txt
Fetching key from https://api.travis-ci.org/repos/dlenski/travis-encrypt-sh/key ...
Encrypting with openssl rsautl ...
```

Now `base64.txt` contains a value that can be directly pasted into this repository's `.travis.yml`
(in order to convey a secret value to the Travis-CI build system without leaking it publicly in this
repository), as in:

```yaml
deploy:
  password:
    secure: "contents of base64.txt go here"
```

## Inspired by…

[My frustrations here](https://github.com/travis-ci/travis-ci/issues/2982#issuecomment-358873469)
