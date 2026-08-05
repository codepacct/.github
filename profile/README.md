<p align="center">
  <img src="https://raw.githubusercontent.com/eleven-smg/codepact-core/main/assets/codepact-banner.svg" alt="Codepact" width="860">
</p>

## A deployed contract only ever hands you a number

When a Soroban call fails, the client does not get a message. It gets an
integer. `300`.

That integer is a promise: it means one specific thing, it means the same thing
next release, and no other contract in the protocol means something different by
it. Nothing in the toolchain enforces that promise. `rustc` will catch a code
reused inside one enum, eventually, after a long build. It will never notice
that your Router and your Factory both claim `300`, or that inserting one
variant renumbered every code below it and broke every integrator at once.

**Codepact makes that promise explicit and enforces it in CI.**

## What we are building

| Repository | What it is |
| --- | --- |
| [`codepact-core`](https://github.com/eleven-smg/codepact-core) | The analyzer and library. Parses `#[contracterror]` enums across a workspace, builds one registry of every code, fails the build on collisions. Zero runtime dependencies, Node 20+. |
| `codepact-cli` | Standalone distributable CLI, with workspace discovery and the generated registry as a committed artefact. |
| `codepact-action` | A GitHub Action, so a contract repo gets the check with three lines of YAML and findings annotated on the diff. |
| `codepact-sdk` | Typed client helpers so an application can map a returned code back to the contract and variant that produced it. |

## Principles

- **A false negative is a security bug.** Teams gate merges on this. A missed
  collision is treated with the same seriousness as a vulnerability, not as a
  nice-to-have.
- **No runtime dependencies.** These tools run inside contract CI jobs where
  nothing is installed and no Rust toolchain is available.
- **Every finding must be actionable.** A message says what is wrong, where, and
  why it matters to a caller. No unexplained rule names.
- **Every change lands through a pull request**, including the maintainer's own.
- **Adoption must be possible.** A mature protocol with existing collisions can
  baseline what exists and never regress, rather than face a red build on day
  one and delete the tool.

## Contributing

Issues labelled `good first issue` are real parser gaps with a clear expected
behaviour and an obvious place to add a test. They need no prior knowledge of
the codebase.

Start with the contributing guide in
[`codepact-core`](https://github.com/eleven-smg/codepact-core/blob/main/CONTRIBUTING.md).

---

<sub>Built for the Soroban and Stellar contract ecosystem. MIT licensed.</sub>
