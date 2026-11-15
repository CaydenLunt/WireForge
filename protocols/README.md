# Protocol registry

This directory contains the protocol registry and independent protocol submodules. The hub tracks this registry and each submodule commit; each checkout tracks its own implementation. See the [workspace setup](../docs/architecture/overview.md) for cloning and Git commands. Repository names remain plain text where actual URLs are not yet known.

| Protocol | Repository | Relevant RFCs | Status |
|---|---|---|---|
| TFTP | [WireForge-TFTP](https://github.com/CaydenLunt/WireForge-TFTP) | RFC 1350, 2347, 2348, 2349, 7440 | Initial development |
| DNS | TBD | RFC 1034, 1035 | Planned |
| HTTP/1.1 | TBD | RFC 9110, 9112 | Planned |
| TCP | TBD | RFC 9293 | Under consideration |

TFTP is the first implementation, registered at `protocols/wireforge-tftp/` relative to the hub root. The tracked update, [23c0dbc](https://github.com/CaydenLunt/WireForge-TFTP/commit/23c0dbc5513057c841545d1dee49cfcaa8041eb1), introduces a C ACK-validation scaffold and CMake warning settings for GCC and Clang-family compilers. The [codec](wireforge-tftp/src/protocol/codec.c) checks packet length, opcode, and input/output pointers, but `decode_ack` does not yet decode or write the block number even when it returns true. CMake has no build targets, and the repository has no automated tests yet. Client/server transfers and option extensions remain planned.

These RFC lists are starting points; each repository must review updates, errata, and dependencies under the [compliance policy](../docs/standards/compliance-policy.md).

Initial development means partial implementation exists, without a complete protocol or verified compliance claim. Planned means intended work with no implementation claimed here. Under consideration means evaluation only, with no implementation commitment. Changes in status require supporting evidence and an update to the [roadmap](../ROADMAP.md).

Use the [contribution guidelines](../CONTRIBUTING.md) to propose additions. Return to the [project overview](../README.md).
