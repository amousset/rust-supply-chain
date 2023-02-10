# Using dependencies

cargo makes it really easy to use dependencies, so the Rust ecosystem tends
to use a lot of them.
This comes with security risks, and we'll see how to mitigate them.

## Choosing dependencies

### Risks

* vulnerabilities
* malicious crates or releases
  * typo squatting (e.g. [rustdecimal](https://blog.rust-lang.org/2022/05/10/malicious-crate-rustdecimal.html))
  * build.rs/proc macros risks
* (lack of) maintenance
* license compliance (not directly linked to security but shared tooling)

### Minimizing dependencies

* minimize dependencies (limit features, tools to explore dependency tree, etc.)
* number of dependencies != attack surface (cargo supply-chain)

### Assessing a dependency

* evaluate a crate
  * [check list by Embark](https://gist.github.com/repi/d98bf9c202ec567fd67ef9e31152f43f)
* cargo crev
* cargo vet
* `unsafe` code management (cargo-geiger, etc.)

## Maintaining dependencies

* Cargo.lock for binaries
* vuln monitoring with cargo audit/deny
* regular updates (to stay on maintained versions)
  * cargo outdated
  * dependabot