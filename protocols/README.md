# Protocol registry

This directory contains the protocol registry and independent protocol submodules. The hub tracks this registry and each submodule commit; each checkout tracks its own implementation. See the [workspace setup](../docs/architecture/overview.md) for cloning and Git commands. Repository names remain plain text where actual URLs are not yet known.

| Protocol | Repository | Relevant RFCs | Status |
|---|---|---|---|
| TFTP | [WireForge-TFTP](https://github.com/CaydenLunt/WireForge-TFTP) | RFC 1350, 2347, 2348, 2349, 7440 | Initial development |
| DNS | TBD | RFC 1034, 1035 | Planned |
| HTTP/1.1 | TBD | RFC 9110, 9112 | Planned |
| TCP | TBD | RFC 9293 | Under consideration |

TFTP is the first implementation, registered at `protocols/wireforge-tftp/` relative to the hub root. The selected checkout, [2d3d362](https://github.com/CaydenLunt/WireForge-TFTP/commit/2d3d362266e1cbcbc299aeda8ba87d329a982886), matches upstream `main` as checked on November 21, 2026.

The C [codec](wireforge-tftp/src/protocol/codec.c) uses separate ACK and DATA packet structures. It validates pointers, lengths, and opcodes before decoding network-order block numbers. ACK requires four bytes; DATA accepts four through 516 bytes and exposes a borrowed payload pointer and length (0 through 512 bytes). Initialization helpers validate packets without decoding their block numbers. Rejected inputs leave destination fields unchanged. Callers retain ownership of the input buffer and must keep it readable while decoding or accessing payloads.

The [ACK tests](wireforge-tftp/tests/unit/test_codec_ack.c) cover byte order, boundary values, invalid lengths and opcodes, null pointers, and output preservation. The [packet contract test](wireforge-tftp/tests/unit/test_codec_packet.c) covers initialization, DATA validation, every valid payload length, empty DATA, and payload-byte preservation. GitHub Actions configures Ubuntu GCC and Clang builds. UDP transport, client/server transfers, packet encoding, RRQ/WRQ/ERROR handling, and option extensions remain planned. See the [Git workflow](../docs/architecture/overview.md) when recording an update.

### Running the TFTP tests

With CMake 3.16 or newer and a C99-capable C compiler installed, run from the hub root:

```sh
cmake -S protocols/wireforge-tftp -B protocols/wireforge-tftp/build -DBUILD_TESTING=ON -DCMAKE_BUILD_TYPE=Debug
cmake --build protocols/wireforge-tftp/build --config Debug
ctest --test-dir protocols/wireforge-tftp/build -C Debug --output-on-failure
```

The `ctest --test-dir` option requires CMake 3.20 or newer; with older versions, run `ctest -C Debug --output-on-failure` from the build directory instead. In a POSIX shell, the equivalent helper is `sh protocols/wireforge-tftp/run-tests.sh`. CMake builds `test_codec_ack` and `test_codec_packet`, registering ten CTest entries: nine individually named ACK tests, such as `decode_ack_rejects_invalid_opcode`, and `codec_packet_contract`. These focused tests do not establish complete TFTP compliance. See the [TFTP development guide](wireforge-tftp/docs/development.md) for CI, test coverage, and known limitations.

These RFC lists are starting points; each repository must review updates, errata, and dependencies under the [compliance policy](../docs/standards/compliance-policy.md).

Initial development means partial implementation exists, without a complete protocol or verified compliance claim. Planned means intended work with no implementation claimed here. Under consideration means evaluation only, with no implementation commitment. Changes in status require supporting evidence and an update to the [roadmap](../ROADMAP.md).

Use the [contribution guidelines](../CONTRIBUTING.md) to propose additions. Return to the [project overview](../README.md).
