# Project roadmap

Statuses describe repository deliverables, not RFC compliance. Complete means the named deliverable exists; planned means work has not been completed. Evaluation does not commit the project to an implementation. No delivery dates are committed.

## Phase 1 — Foundation: complete

- [x] Establish the root repository structure.
- [x] Document engineering standards and compliance expectations.
- [x] Establish contribution guidelines and a protocol request form.
- [x] Create the protocol registry.

This phase delivers documentation and configuration only.

## Phase 2 — TFTP: initial development

- [x] Establish the independent [TFTP repository](https://github.com/CaydenLunt/WireForge-TFTP) and register it as a submodule at `protocols/wireforge-tftp/` for local development.
- [x] Add the initial C ACK-validation scaffold and CMake compiler warning settings ([23c0dbc](https://github.com/CaydenLunt/WireForge-TFTP/commit/23c0dbc5513057c841545d1dee49cfcaa8041eb1)).
- [x] Complete ACK block-number decoding, add a CMake/CTest target, and add unit tests for validation and decoding behavior ([4ce0f95](https://github.com/CaydenLunt/WireForge-TFTP/commit/4ce0f958eed78b0faf9484b0ce4016369937c302)).
- [x] Add separate ACK/DATA packet types, validated initialization, DATA block-number decoding and borrowed payload access, plus a packet contract test (ten CTest entries total; [2d3d362](https://github.com/CaydenLunt/WireForge-TFTP/commit/2d3d362266e1cbcbc299aeda8ba87d329a982886)).
- [ ] Implement core RFC 1350 functionality against an agreed scope and requirements matrix.
- [x] Register nine ACK cases individually in CTest and add Ubuntu GCC/Clang CI. See the [development guide](protocols/wireforge-tftp/docs/development.md) for coverage and limitations.
- [ ] Implement option negotiation and extensions from RFCs 2347, 2348, 2349, and 7440 incrementally.
- [ ] Develop automated compliance tests with requirement traceability.
- [ ] Perform interoperability and fault-injection testing and publish reproducible evidence.

## Phase 3 — Additional Protocols: planned

- [ ] Evaluate DNS and HTTP/1.1 implementations, including scope and maintenance cost.
- [ ] Identify reusable engineering patterns from completed work.
- [ ] Consider extracting shared testing tools where multiple implementations demonstrate a need.

## Phase 4 — Advanced Networking: under consideration

- [ ] Evaluate implementing TCP.
- [ ] Explore deeper transport-layer behavior.
- [ ] Expand cross-protocol interoperability testing where relevant implementations exist.

See the [registry](protocols/README.md) for protocol status and the [compliance policy](docs/standards/compliance-policy.md) for evidence requirements.
