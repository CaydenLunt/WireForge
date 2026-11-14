# WireForge

**Network protocols built from the specification, tested on the wire.**

WireForge is an open-source collection of network protocol implementations developed from scratch using official RFC specifications.

The project aims to explore the underlying mechanics of network communication through hands-on development, emphasizing standards compliance, interoperability, reliability, and rigorous testing.

Rather than relying on existing protocol libraries, WireForge focuses on implementing protocol logic directly to develop a deeper understanding of packet structures, state machines, error handling, concurrency, and network behavior.

## Project Goals

- **Standards Compliance:** Implement protocols according to their published RFC specifications.
- **Interoperability:** Ensure implementations communicate correctly with established clients and servers.
- **Reliability:** Handle packet loss, retransmissions, timeouts, malformed packets, and unexpected network conditions.
- **Testing:** Develop comprehensive unit, integration, and fault-injection tests.
- **Observability:** Provide meaningful logging and diagnostics for troubleshooting protocol behavior.
- **Documentation:** Document implementation decisions, protocol behavior, and compliance with relevant specifications.

## Protocol Implementations

| Protocol | Description | Status |
|---|---|---|
| TFTP | Trivial File Transfer Protocol | Planned — First implementation |
| DNS | Domain Name System | Planned |
| HTTP/1.1 | Hypertext Transfer Protocol | Planned |
| TCP | Transmission Control Protocol | Under consideration |

Additional protocols may be added as the project evolves.

## First Project: TFTP

The first implementation will focus on the Trivial File Transfer Protocol (TFTP), a lightweight file transfer protocol operating over UDP.

### Planned Features

- TFTP client and server implementations
- Read and write requests (RRQ/WRQ)
- DATA, ACK, and ERROR packet handling
- Independent concurrent transfer sessions
- Timeout and retransmission handling
- Transfer error detection and reporting
- Structured logging and diagnostics
- Interoperability testing against existing implementations
- Packet loss and fault-injection testing

### Relevant Specifications

- [RFC 1350](https://www.rfc-editor.org/rfc/rfc1350) — The TFTP Protocol (Revision 2)
- [RFC 2347](https://www.rfc-editor.org/rfc/rfc2347) — TFTP Option Extension
- [RFC 2348](https://www.rfc-editor.org/rfc/rfc2348) — TFTP Blocksize Option
- [RFC 2349](https://www.rfc-editor.org/rfc/rfc2349) — TFTP Timeout Interval and Transfer Size Options
- [RFC 7440](https://www.rfc-editor.org/rfc/rfc7440) — TFTP Windowsize Option

## Development Philosophy

WireForge follows a specification-driven development approach.

Each protocol implementation will prioritize correctness over convenience, with an emphasis on understanding why the protocol operates as specified.

Implementations will be developed incrementally, validated against documented protocol behavior, and tested under both normal and adverse network conditions.

The goal is not simply to create working implementations, but to build implementations whose behavior can be understood, verified, and explained.

## Project Status

**Early Development**

WireForge is currently in the planning and initial development stage. APIs, project structure, and implementation details are subject to change.

## Contributing

Contributions, bug reports, suggestions, and discussions are welcome as the project develops.

## License

WireForge is licensed under the MIT License. See [LICENSE](LICENSE) for details.
