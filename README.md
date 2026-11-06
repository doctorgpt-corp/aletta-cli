# The Ask Aletta CLI

`aletta` drives the Ask Aletta sandbox from a terminal: conversations, tasks, patient
contexts and every scripted scenario, with a sandbox key from the Platform.

## Install

```sh
curl -fsSL https://platform.askaletta.com/cli | sh
```

The script installs `aletta` to `~/.local/bin` (or `ALETTA_INSTALL_DIR`) without `sudo`,
and `ALETTA_VERSION=<version>` pins a release. Builds exist for macOS (Apple silicon and
Intel) and Linux (x86_64 and arm64, static). On Windows, install it inside WSL.

Then save a sandbox key from the Platform and play a scenario:

```sh
pbpaste | aletta keys save
aletta scenarios play answer.citations
```

`aletta update` installs the newest release.

## Verify a download

Each release carries `SHA256SUMS` and its minisign signature `SHA256SUMS.minisig`.

```sh
minisign -Vm SHA256SUMS -P RWS+Ox5DM7U90MnKOTT0xZXhEfJI/mxRDlo02Q5oeWSPJ3xBmffA89iJ
shasum -a 256 -c SHA256SUMS --ignore-missing    # macOS
sha256sum -c SHA256SUMS --ignore-missing        # Linux
```

The release public key:

```
RWS+Ox5DM7U90MnKOTT0xZXhEfJI/mxRDlo02Q5oeWSPJ3xBmffA89iJ
```

`aletta update` checks the signature against this key, built into the binary, before it
installs anything.

## Documentation and support

The documentation is at https://platform.askaletta.com/docs. Support goes through the
Platform; this repository holds releases only and takes no issues.
