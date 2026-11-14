# Architecture overview

WireForge is a collection of independent protocol repositories developed within this root hub's workspace. Protocol repositories are cloned under `protocols/`. All protocol implementations are currently planned or under consideration; see the [registry](../../protocols/README.md).

## Root repository

The hub coordinates development across all protocol projects through the project overview, roadmap, protocol registry, contribution guidance, and common engineering policies. Its working directory contains the protocol checkouts, while its Git history tracks the shared documentation and configuration. There is currently no combined build or synchronized release train.

## Protocol repositories

Use lowercase `wireforge-<protocol>` names, such as `wireforge-tftp` and, if created, `wireforge-dns`. Record actual repository URLs in the registry only after they are known.

Each repository owns its implementation, public interfaces, specification inventory, compliance matrix, tests, interoperability results, documentation, and release notes. It chooses a language and toolchain appropriate to the protocol and maintainers; no project-wide implementation language is mandated.

Each repository documents its own reproducible build and test commands, supported environments, dependencies, versioning policy, and release procedure. Builds, test automation, tags, and releases are independent. A release of one protocol does not require releasing this hub or another protocol. Published claims must follow the [compliance policy](../standards/compliance-policy.md).

## Shared tooling

Keep tools local to the implementation that needs them initially. Document useful patterns here when they become repeatable. Extract a shared library or testing tool only when multiple implementations demonstrate a concrete need and agree on its scope, ownership, compatibility policy, and maintenance cost. Consume any eventual shared packages through explicit versions rather than implicit coupling to another repository's working tree.

## Local workspace and Git workflow

Clone each protocol repository directly into `protocols/` using its documented remote. For TFTP, run this from the hub root if the checkout does not already exist:

```sh
git clone https://github.com/CaydenLunt/WireForge-TFTP.git protocols/wireforge-tftp
```

```text
WireForge/
├── .git/
├── docs/
└── protocols/
    ├── README.md
    └── wireforge-tftp/
        └── .git/
```

These are ordinary nested Git clones, each with its own history, branches, remote, and configuration. The hub ignores `/protocols/wireforge-*/` so protocol files are committed in their owning repositories. The current setup does not use Git submodule registration or pin protocol revisions in the hub. Cloning the hub alone does not fetch protocol repositories; clone the projects needed for your work separately into the paths shown here.

Work from the hub directory and target the appropriate repository explicitly:

```sh
git status
git -C protocols/wireforge-tftp status
git -C protocols/wireforge-tftp remote -v
```

Run builds and tests using each protocol repository's instructions and working directory. Commit hub policy changes in the hub and protocol changes in their own repository. A hub commit or push does not include changes from the nested clones. Coordinate changes spanning projects through linked issues and pull requests.

See the [roadmap](../../ROADMAP.md) for sequencing and [contribution guidelines](../../CONTRIBUTING.md) for proposals.
