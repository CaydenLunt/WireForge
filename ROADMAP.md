# Project roadmap

Statuses describe repository deliverables, not RFC compliance. Complete means the named deliverable exists; planned means work has not been completed. Evaluation does not commit the project to an implementation. No delivery dates are committed.

## Phase 1 — Foundation: complete

- [x] Establish the root repository structure.
- [x] Document engineering standards and compliance expectations.
- [x] Establish contribution guidelines and a protocol request form.
- [x] Create the protocol registry.

This phase delivers documentation and configuration only.

## Phase 2 — TFTP: repository established; implementation planned

- [x] Establish the independent [TFTP repository](https://github.com/CaydenLunt/WireForge-TFTP) and clone it into `protocols/wireforge-tftp/` for local development.
- [ ] Implement core RFC 1350 functionality against an agreed scope and requirements matrix.
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
