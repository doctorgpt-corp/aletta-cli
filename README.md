# The Ask Aletta CLI

`aletta` is the command line for the Ask Aletta Platform. It manages your organization's
setup (sandboxes, API keys and management tokens) and calls the Ask Aletta API
(conversations, tasks, patient contexts and every scripted scenario), from a terminal or
in CI.

This release covers the sandbox. The test and live environments, and the rest of the
Platform's controls, come to the same CLI in later releases.

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
