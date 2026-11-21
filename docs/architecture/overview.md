# Architecture overview

WireForge is a collection of independent protocol repositories developed within this root hub's workspace. Protocol repositories are registered as Git submodules under `protocols/`. TFTP is in initial development with C ACK/DATA decoding, payload access, and unit tests; other protocols remain planned or under consideration. See the [registry](../../protocols/README.md) for implementation limits.

## Root repository

The hub coordinates development across all protocol projects through the project overview, roadmap, protocol registry, contribution guidance, and common engineering policies. Its working directory contains the protocol checkouts, while its Git history tracks shared documentation, configuration, and selected protocol commits. There is currently no combined build or synchronized release train.

## Protocol repositories

Use lowercase `wireforge-<protocol>` names, such as `wireforge-tftp` and, if created, `wireforge-dns`. Record actual repository URLs in the registry only after they are known.

Each repository owns its implementation, public interfaces, specification inventory, compliance matrix, tests, interoperability results, documentation, and release notes. It chooses a language and toolchain appropriate to the protocol and maintainers; no project-wide implementation language is mandated.

Each repository documents its own reproducible build and test commands, supported environments, dependencies, versioning policy, and release procedure. Builds, test automation, tags, and releases are independent. A release of one protocol does not require releasing this hub or another protocol. Published claims must follow the [compliance policy](../standards/compliance-policy.md).

## Shared tooling

Keep tools local to the implementation that needs them initially. Document useful patterns here when they become repeatable. Extract a shared library or testing tool only when multiple implementations demonstrate a concrete need and agree on its scope, ownership, compatibility policy, and maintenance cost. Consume any eventual shared packages through explicit versions rather than implicit coupling to another repository's working tree.

## Local workspace and Git workflow

Protocol repositories are Git submodules under `protocols/`. Each retains its own history, branches, remote, and configuration. The hub records paths and URLs in `.gitmodules` and tracks a specific commit of each protocol. GitHub displays these as linked repositories once the hub changes are committed and pushed.

Clone the hub and its registered submodules together:

```sh
git clone --recurse-submodules https://github.com/CaydenLunt/WireForge.git
```

For an existing hub checkout, initialize the submodules or update them to the commits recorded by the hub:

```sh
git submodule update --init --recursive
```

Check and save protocol work before updating. Submodule updates normally check out a detached HEAD; switch to an appropriate existing branch or create a development branch before making changes. Git metadata normally lives under the hub's `.git/modules/`, referenced by a `.git` file in each submodule checkout.

Inspect the hub and protocol independently:

```sh
git status
git submodule status
git -C protocols/wireforge-tftp status
git -C protocols/wireforge-tftp remote -v
```

Run builds and tests in the protocol's working directory using its instructions. Commit and push protocol changes to their own repository first. Then run `git add protocols/wireforge-tftp` in the hub and commit and push that pointer update. A hub commit does not include protocol source changes, and a hub push alone does not publish protocol commits.

Register future protocols with `git submodule add <actual-repository-url> protocols/wireforge-<protocol>`. Include both `.gitmodules` and the new protocol pointer in the hub change. Coordinate work spanning projects through linked issues and pull requests.

See the [roadmap](../../ROADMAP.md) for sequencing and [contribution guidelines](../../CONTRIBUTING.md) for proposals.
