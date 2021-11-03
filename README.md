# Update supported Bee action

[![](https://img.shields.io/badge/made%20by-Swarm-blue.svg?style=flat-square)](https://swarm.ethereum.org/)
[![standard-readme compliant](https://img.shields.io/badge/standard--readme-OK-brightgreen.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme)

> Action that replaces the supported Bee node's version based on bee-js setting.

**Warning: This project is in beta state. There might (and most probably will) be changes in the future to its API and working. Also, no guarantees can be made about its stability, efficiency, and security at this stage.**

## Table of Contents

- [Usage](#usage)
- [Action inputs](#action-inputs)
- [Action outputs](#action-outputs)
- [Contribute](#contribute)
- [License](#license)

## Usage

Have some file(s) which have somewhere in them specified the supported version. Replace the version with: `<!-- SUPPORTED_BEE_START -->1.2.0<!-- SUPPORTED_BEE_END -->`. 
This is a comment in Markdown which is used to mark where the replacement should happen for the action. 

**The project has to have `package-lock.json` file which in some of its direct or indirect dependencies has `bee-js`.**

```yaml
name: Update supported Bee version

on:
  push:
    branches:
      - 'master'

jobs:
  check:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Check and update the Bee version
        uses: ethersphere/upload-supported-bee-action@master
        with:
          token: ${{ secrets.PTA_TOKEN }}
          files: README.md
```

## Action inputs

| Name | Description | Default |
| --- | --- | --- |
| `token` | Token to be used for creating of the updating PR. | `GITHUB_TOKEN` |
| `files` | Files delimited by space to search&replace the version. | `README.md` |

## Action outputs

| Name | Description |
| --- | --- |
| `version` | The new Bee supported version |

## Contribute

There are some ways you can make this module better:

- Consult our [open issues](https://github.com/ethersphere/update-supported-bee-action/issues) and take on one of them
- Help our tests reach 100% coverage!
- Join us in our [Discord chat](https://discord.gg/wdghaQsGq5) in the #develop-on-swarm channel if you have questions or want to give feedback

## Maintainers

- [auhau](https://github.com/auhau)

## License

[BSD-3-Clause](./LICENSE)

