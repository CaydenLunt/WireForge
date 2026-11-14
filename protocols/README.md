# Protocol registry

This directory contains the protocol registry and local independent protocol checkouts. The hub tracks this registry; each checkout tracks its own implementation. See the [workspace setup](../docs/architecture/overview.md) for cloning and Git commands. Repository names remain plain text where actual URLs are not yet known.

| Protocol | Repository | Relevant RFCs | Status |
|---|---|---|---|
| TFTP | [WireForge-TFTP](https://github.com/CaydenLunt/WireForge-TFTP) | RFC 1350, 2347, 2348, 2349, 7440 | Planned |
| DNS | TBD | RFC 1034, 1035 | Planned |
| HTTP/1.1 | TBD | RFC 9110, 9112 | Planned |
| TCP | TBD | RFC 9293 | Under consideration |

TFTP is the first intended implementation, with its repository established and its local checkout at `protocols/wireforge-tftp/` relative to the hub root. Implementation remains planned. These RFC lists are starting points; each repository must review updates, errata, and dependencies under the [compliance policy](../docs/standards/compliance-policy.md).

Planned means intended work with no implementation claimed here. Under consideration means evaluation only, with no implementation commitment. Changes in status require supporting evidence and an update to the [roadmap](../ROADMAP.md).

Use the [contribution guidelines](../CONTRIBUTING.md) to propose additions. Return to the [project overview](../README.md).
