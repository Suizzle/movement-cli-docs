---
title: "Use the Movement CLI"
id: "use-movement-cli"
---

# Use the Movement CLI

The `movement` tool is a command line interface (CLI) for developing on the Movement blockchain, debugging, and for node operations. This document describes how to use the `movement` CLI tool. To download or build the CLI, follow [Install Movement CLI](../install-cli/index.md).

For example on how to use specific commands, see the following documents:
- [Account](./cli-account.md)
- [Configuration](./cli-config.md)
- [Faucet](./cli-faucet.md)
- [Genesis](./cli-genesis.md)
- [Governance](./cli-governance.md)
- [Help](./cli-help.md)
- [Info](./cli-info.md)
- [Init](./cli-init.md)
- [Key](./cli-key.md)
- [Move](./cli-move.md)
- [Multisig](./cli-multisig.md)
- [Node](./cli-node.md)
- [Stake](./cli-stake.md)
- [Update](./cli-update.md)

## Command line help

Command line help is available. Type `movement help` or `movement --help` to see the available command options. See below the usage output from `movement --help`:

```bash
USAGE:
    movement <SUBCOMMAND>

OPTIONS:
    -h, --help       Print help information
    -V, --version    Print version information

SUBCOMMANDS:
    account       Tool for interacting with accounts
    config        Tool for interacting with configuration of the Movement CLI tool
    genesis       Tool for setting up an Movement chain Genesis transaction
    governance    Tool for on-chain governance
    help          Print this message or the help of the given subcommand(s)
    info          Show build information about the CLI
    init          Tool to initialize current directory for the movement tool
    key           Tool for generating, inspecting, and interacting with keys
    move          Tool for Move related operations
    multisig      Tool for interacting with multisig accounts
    node          Tool for operations related to nodes
    stake         Tool for manipulating stake and stake pools
    update        Update the CLI itself
```

### Command-specific help

Command-specific help is also available. For example, see below the usage output from `movement move --help`:

```bash

USAGE:
    movement move <SUBCOMMAND>

OPTIONS:
    -h, --help       Print help information
    -V, --version    Print version information

SUBCOMMANDS:
    build-publish-payload
            Build a publication transaction payload and store it in a JSON output file
    clean
            Cleans derived artifacts of a package
    compile
            Compiles a package and returns the associated ModuleIds
    compile-script
            Compiles a Move script into bytecode
    coverage
            Computes coverage for a package
    create-resource-account-and-publish-package
            Publishes the modules in a Move package to the Movement blockchain under a resource account
    disassemble
            Disassemble the Move bytecode pointed to
    document
            Documents a Move package
    download
            Downloads a package and stores it in a directory named after the package
    help
            Print this message or the help of the given subcommand(s)
    init
            Creates a new Move package at the given location
    list
            Lists information about packages and modules on-chain for an account
    prove
            Proves a Move package
    publish
            Publishes the modules in a Move package to the Movement blockchain
    run
            Run a Move function
    run-script
            Run a Move script
    test
            Runs Move unit tests for a package
    verify-package
            Downloads a package and verifies the bytecode
    view
            Run a view function
```

### Sub-command help

Help for sub-commands is also available. For example, see below the usage output from `movement move compile --help`:

```bash

Usage: movement move compile [OPTIONS]

Options:
      --save-metadata
          Save the package metadata in the package's build directory
          
          If set, package metadata should be generated and stored in the package's build directory. This metadata can be used to construct a transaction to publish a package.

      --included-artifacts <INCLUDED_ARTIFACTS>
          Artifacts to be generated when building the package
          
          Which artifacts to include in the package. This can be one of `none`, `sparse`, and `all`. `none` is the most compact form and does not allow to reconstruct a source package from chain; `sparse` is the minimal set of artifacts needed to reconstruct a source package; `all` includes all available artifacts. The choice of included artifacts heavily influences the size and therefore gas cost of publishing: `none` is the size of bytecode alone; `sparse` is roughly 2 times as much; and `all` 3-4 as much.
          
          [default: sparse]
          [possible values: none, sparse, all]

      --dev
          Enables dev mode, which uses all dev-addresses and dev-dependencies
          
          Dev mode allows for changing dependencies and addresses to the preset [dev-addresses] and [dev-dependencies] fields.  This works both inside and out of tests for using preset values.
          
          Currently, it also additionally pulls in all test compilation artifacts

      --package-dir <PACKAGE_DIR>
          Path to a move package (the folder with a Move.toml file)

      --output-dir <OUTPUT_DIR>
          Path to save the compiled move package
          
          Defaults to `<package_dir>/build`

      --named-addresses <NAMED_ADDRESSES>
          Named addresses for the move binary
          
          Example: alice=0x1234, bob=0x5678
          
          Note: This will fail if there are duplicates in the Move.toml file remove those first.
          
          [default: ]

      --skip-fetch-latest-git-deps
          Skip pulling the latest git dependencies
          
          If you don't have a network connection, the compiler may fail due to no ability to pull git dependencies.  This will allow overriding this for local development.

      --bytecode-version <BYTECODE_VERSION>
          Specify the version of the bytecode the compiler is going to emit

      --compiler-version <COMPILER_VERSION>
          Specify the version of the compiler
          
          [possible values: v1, v2]

      --skip-attribute-checks
          Do not complain about unknown attributes in Move code

  -h, --help
          Print help (see a summary with '-h')

  -V, --version
          Print version
```

## CLI information

Run the `movement info` command to get the CLI information for debugging purposes. See an example output of the `movement info` command:

```bash
{
  "Result": {
    "build_branch": "",
    "build_cargo_version": "cargo 1.71.2 (1a737af0c 2023-08-07)",
    "build_clean_checkout": "true",
    "build_commit_hash": "",
    "build_is_release_build": "true",
    "build_os": "macos-aarch64",
    "build_pkg_version": "2.1.0",
    "build_profile_name": "cli",
    "build_rust_channel": "",
    "build_rust_version": "rustc 1.71.1 (eb26296b5 2023-08-03) (built from a source tarball)",
    "build_tag": "",
    "build_time": "2023-08-24 21:13:40 +00:00",
    "build_using_tokio_unstable": "true"
  }
}
```

