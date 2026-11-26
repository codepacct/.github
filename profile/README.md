<p align="center">
  <img src="https://raw.githubusercontent.com/codepacct/codepact-core/main/assets/codepact-banner.svg" alt="Codepact" width="860">
</p>

# Codepact

Codepact is an early-stage open-source toolkit for managing error-code
allocations in Stellar Soroban smart-contract workspaces. It helps developers
find repeated codes and review the numeric interface that clients rely on.

## Projects

| Repository | Purpose |
| --- | --- |
| [codepact-core](https://github.com/codepacct/codepact-core) | A Node.js analyzer and CLI that scans supported `#[contracterror]` enums and reports error-code findings. |
| [codepact-action](https://github.com/codepacct/codepact-action) | A GitHub Action that runs the analyzer and reports findings in CI. |
| [codepact-conventions](https://github.com/codepacct/codepact-conventions) | A draft allocation specification, JSON Schema, and configuration validator. |

The projects are related: Core analyzes code, the Action runs a vendored copy
in CI, and Conventions describes allocations that Core can enforce. See each
repository's README for setup, current capabilities, and known limitations.

## Status and roadmap

The tools use lexical analysis rather than a full Rust compiler frontend. A
clean report does not establish that a contract is secure or that every Rust
expression was analyzed. Review the documented limitations before making the
checks mandatory. The Core CLI supports reviewed baselines for incremental adoption; the Action
does not yet support them. See [Action baseline support](https://github.com/codepacct/codepact-action/issues/10).

## Contributing

Contributions are welcome. Browse the open issues in
[Core](https://github.com/codepacct/codepact-core/issues),
[Action](https://github.com/codepacct/codepact-action/issues), or
[Conventions](https://github.com/codepacct/codepact-conventions/issues), and
read that repository's contribution and security policies before starting.
Please use the private reporting guidance for suspected security issues.

Each repository describes its declared MIT license and contribution workflow.
