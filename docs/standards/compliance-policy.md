# Standards and compliance policy

WireForge develops from specifications and supports claims with reproducible evidence. This policy defines future implementation expectations; it does not certify any implementation.

## Specification inventory

Before implementing a protocol, record applicable RFC numbers, official links, sections, document status, updates, obsoleting documents, and relevant errata with their disposition and review date. Review normative dependencies and host requirements as well as the main protocol RFC. State the supported roles, modes, extensions, platforms, and exclusions. The [registry](../../protocols/README.md) is a starting list, not an exhaustive applicability assessment.

## Requirements and traceability

Use the terminology defined in [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) and clarified by [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174) when the source specification adopts it. MUST and MUST NOT express absolute requirements or prohibitions; SHOULD and SHOULD NOT allow justified exceptions after evaluating their consequences; MAY describes an option. Uppercase keywords have the special BCP 14 meanings. Older specifications can express binding behavior without these keywords: interpret their prose in context, and record that interpretation instead of inventing an uppercase requirement.

Give each requirement a stable ID and track its source section, requirement level or prose classification, applicability, implementation component, test identifiers, result evidence, and disposition. Separate normative behavior from explanatory examples and implementation advice. Track mandatory, recommended, and optional behavior, including requirements conditional on enabling an extension.

Use explicit states such as planned, implemented but unverified, verified for a named revision, unsupported optional feature, and deviation. A passing test must not silently change other untested requirements to verified. Document each deviation with technical justification, interoperability impact, affected versions, and review outcome. Unsupported optional features need an explicit scope entry and tests of the specified fallback behavior where applicable. An unmet mandatory requirement prevents an unqualified compliance claim.

## Example TFTP compliance matrix

These illustrative rows cover a small subset of [RFC 1350](https://www.rfc-editor.org/rfc/rfc1350), not a complete audit. Components and tests below are proposed names, not existing artifacts. Every row is unimplemented and unverified. Base-protocol behavior below assumes no negotiated extensions.

| ID | Source | Requirement / classification | Proposed component | Proposed test | Status / evidence |
|---|---|---|---|---|---|
| TFTP-001 | RFC 1350 §4 | Initial WRQ response uses ACK block zero; protocol rule in prose | Session state machine | Assert ACK(0) after accepted WRQ | Planned / none |
| TFTP-002 | RFC 1350 §5 | DATA payload contains 0–512 bytes; protocol rule in prose | Packet codec | Check valid bounds and oversized input | Planned / none |
| TFTP-003 | RFC 1350 §6 | A short final DATA packet is acknowledged; protocol rule in prose | Transfer completion | Empty file and exact-block-size transfer termination | Planned / none |
| TFTP-004 | RFC 1350 §6 | Receiver is encouraged to linger after final ACK; recommendation in prose | Session cleanup | Drop final ACK and resend final DATA | Planned / none |

Before TFTP development, expand the inventory to the extensions listed in the registry and relevant dependencies. Record option support individually and distinguish base-protocol tests from negotiated-option tests.

## Testing expectations

- **Automated compliance:** Map requirements to codec, state-machine, integration, and boundary tests. Include expected wire behavior and deterministic reproduction commands.
- **Interoperability:** Exercise each supported role against identified independent implementations. Record peer versions, settings, platform, direction, negotiated features, commands, and results. Successful transfers alone do not prove compliance.
- **Negative testing:** Cover truncated and oversized packets, invalid fields, unexpected states, and malformed input. Assert specified error behavior, bounded resource use, and continued process stability. Separate RFC requirements from additional hardening choices.
- **Fault injection:** Exercise loss, duplication, reordering, delay, timeout, peer termination, and relevant local resource failures. Record seeds, fault schedules, limits, and expected recovery or termination so failures are repeatable.

## Evidence required for compliance claims

Before making a claim, reviewers must examine the complete matrix for the declared scope, resolve every applicable mandatory requirement, justify recommendation deviations, and disclose optional-feature exclusions. Link the exact release or commit, test commands and environment, results, interoperability reports, fault-injection results, and known limitations. Preserve enough logs or packet traces to reproduce and assess behavior without publishing private data.

Phrase claims narrowly: identify the RFCs, roles, extensions, version, and tested environments. A test count or coverage percentage is not a substitute for requirement evidence; compliance evidence is not a guarantee of production readiness. Revalidate affected requirements after changes and keep historical release evidence identifiable.
