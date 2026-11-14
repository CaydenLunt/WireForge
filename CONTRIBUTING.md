# Contributing to WireForge

Prioritize correctness, maintainability, and evidence-based engineering decisions. This repository coordinates the project; implementation work belongs in independent protocol repositories.

## Propose a protocol

Open a GitHub issue using the [protocol request form](.github/ISSUE_TEMPLATE/protocol-request.yml). Include official specifications, intended roles and extensions, motivation, likely complexity, and interoperability targets. Check the [registry](protocols/README.md) first. Explain maintenance needs and technical tradeoffs; a proposal is not an implementation commitment. Repository creation and ownership should be agreed before adding an actual URL to the registry.

## Report documentation issues

Open an issue identifying the file and section, the problem, and a suggested correction. Include official RFC section links for technical discrepancies. Small corrections can be proposed directly as focused pull requests. Keep the README, registry, and roadmap consistent when changing status.

## Contribute to an implementation

Initialize protocol submodules under `protocols/wireforge-<protocol>/` with `git submodule update --init --recursive` and follow their own contribution, build, test, and release instructions. See the [workspace setup](docs/architecture/overview.md). Submit protocol code and related tests to the owning repository. Cite RFC numbers and sections, explain interpretations and alternatives, and update its compliance matrix for behavioral changes. The hub tracks each submodule commit; use `git -C protocols/wireforge-tftp status` to inspect TFTP changes. Work on a protocol branch and commit and push its changes first, then stage its updated pointer in the hub. Include `.gitmodules` when registering a new protocol. Coordinate shared plans and standards here, and link related pull requests across repositories.

## Testing expectations

For hub changes, validate issue-form YAML, check relative Markdown links and milestone consistency, and review formatting and technical claims. No protocol build is required here.

For implementations, provide relevant automated tests and regression cases, including malformed inputs and boundary conditions. Supply interoperability and fault-injection evidence appropriate to the change, with reproducible commands, peer versions, and results. Explain tests not run and remaining gaps. Follow the [compliance policy](docs/standards/compliance-policy.md); do not claim compliance from happy-path tests alone.

## Pull requests and review

Keep each pull request focused. Use a descriptive title and explain the problem, resulting behavior, technical justification, related issues, RFC citations, validation performed, and limitations. Update affected documentation alongside changes. Avoid unrelated refactors, dependencies, and generated files. No special commit prefix is required by this hub.

Reviewers assess correctness against the cited specifications, reproducibility of evidence, clarity, maintainability, and scope. Resolve substantive review feedback before merge and document disagreements with evidence. Deviations need explicit reasoning and review, not silent exceptions. Maintainers determine acceptance; proposed status changes should reflect delivered work.

Contributions are intended for distribution under the project's [MIT License](LICENSE).
