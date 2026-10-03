# Termux Security-Tool Installer

This repository currently contains an experimental Termux installer script and setup notes. It does not contain the NodeWeaver application, a web service, or a validated security product.

Use the tools only on networks and devices you own or have explicit written authorization to test.

## Repository contents

- [`termux`](./termux) checks network status with Termux:API, clones Metasploit, Nuclei, and btlejack under `$HOME/opt`, and creates command wrappers under `$HOME/bin`.
- [`Termux pkg install`](./Termux%20pkg%20install) contains setup notes and separate commands for scripts and services hosted outside this repository. Those remote scripts, endpoints, and claims are not included or verified here.
- [`LICENSE`](./LICENSE) contains the license for this repository. The cloned upstream projects have their own licenses and terms.

The `termux` script clones the upstream repositories' current default branches without pinning revisions or verifying signed commits. It does not build the cloned tools or launch scans during installation; the generated wrappers can launch them later.

## Requirements

The setup notes specify Termux and Termux:API from F-Droid, plus these Termux packages:

```sh
pkg install -y git curl jq python ruby termux-api
```

The script uses Termux:API to read local Wi-Fi or telephony information and displays status locally. Its mobile-network fallback stores the carrier name in a variable labelled `IP`; that value is not an IP address.

## Review before use

Read `termux` and review the upstream projects and revisions before running it. The script clones moving default branches, modifies `$HOME/.bashrc`, and installs wrappers in `$HOME/bin`. No rollback or uninstall procedure is provided.

The separate hosted commands in `Termux pkg install` are outside this repository and have not been validated here. Do not execute remote scripts just because they are listed in that file; verify their source and review their contents first.

## Validation status

`bash -n termux` passes as a syntax check. The script has not been run or tested on a Termux device, and no network or device testing has been performed from this repository. No automated test suite or CI configuration is present.
