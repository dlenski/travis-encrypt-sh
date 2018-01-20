# travis-encrypt-sh

Pure-`bash` script to [encrypt values](https://docs.travis-ci.com/user/encryption-keys/)
for use in [Travis-CI](https://travis-ci.org) build scripts.

Requires `curl`, `sed`, and `openssl rsautl` command-line utilities.

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

## License

GPLv3 or later
