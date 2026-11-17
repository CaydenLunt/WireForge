# Protocol registry

This directory contains the protocol registry and independent protocol submodules. The hub tracks this registry and each submodule commit; each checkout tracks its own implementation. See the [workspace setup](../docs/architecture/overview.md) for cloning and Git commands. Repository names remain plain text where actual URLs are not yet known.

| Protocol | Repository | Relevant RFCs | Status |
|---|---|---|---|
| TFTP | [WireForge-TFTP](https://github.com/CaydenLunt/WireForge-TFTP) | RFC 1350, 2347, 2348, 2349, 7440 | Initial development |
| DNS | TBD | RFC 1034, 1035 | Planned |
| HTTP/1.1 | TBD | RFC 9110, 9112 | Planned |
| TCP | TBD | RFC 9293 | Under consideration |

TFTP is the first implementation, registered at `protocols/wireforge-tftp/` relative to the hub root. The tracked update, [45e69c2](https://github.com/CaydenLunt/WireForge-TFTP/commit/45e69c20e77aeae2b21b2b45799dd6ce8d1ca92f), includes C ACK decoding, a CMake/CTest target, unit tests, and a shell test runner. The [codec](wireforge-tftp/src/protocol/codec.c) validates packet length, opcode, and input/output pointers, then writes the 16-bit block number decoded in network byte order. Rejected inputs leave the output unchanged. The [unit tests](wireforge-tftp/tests/unit/test_codec_ack.c) cover byte order, boundary values, invalid lengths and opcodes, null pointers, and output preservation. Client/server transfers and option extensions remain planned.

### Running the TFTP tests

With CMake 3.16 or newer and a C99-capable C compiler installed, run from the hub root:

```sh
cmake -S protocols/wireforge-tftp -B protocols/wireforge-tftp/build -DBUILD_TESTING=ON -DCMAKE_BUILD_TYPE=Debug
cmake --build protocols/wireforge-tftp/build --config Debug
ctest --test-dir protocols/wireforge-tftp/build -C Debug --output-on-failure
```

The `ctest --test-dir` option requires CMake 3.20 or newer; with older versions, run `ctest -C Debug --output-on-failure` from the build directory instead. In a POSIX shell, the equivalent helper is `sh protocols/wireforge-tftp/run-tests.sh`. The CTest test is named `codec_ack`; these focused tests do not establish complete TFTP compliance.

These RFC lists are starting points; each repository must review updates, errata, and dependencies under the [compliance policy](../docs/standards/compliance-policy.md).

Initial development means partial implementation exists, without a complete protocol or verified compliance claim. Planned means intended work with no implementation claimed here. Under consideration means evaluation only, with no implementation commitment. Changes in status require supporting evidence and an update to the [roadmap](../ROADMAP.md).

Use the [contribution guidelines](../CONTRIBUTING.md) to propose additions. Return to the [project overview](../README.md).
