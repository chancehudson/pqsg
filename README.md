# post quantum security group

This document specifies desired outcomes and operational strategies for an engineering team.

## Outcome

The pqsg seeks to produce and benchmark high quality implementations of post quantum secure algorithms and primitives. These implementations should be focused on use in real world protocols like Semaphore, Ethereum, and TLS.

Implementations should be built using libraries that are resistant to timing and memory access attacks, in addition to being cryptographically secure.

In cases where high quality and safe math implementations do not exist the working group should roll it's own implementation with the intent of breaking out such implementations into publicly shared, re-usable math libraries.

The pqsg should provide reports comparing the concrete computational and communication complexity for any algorithm/primitive that is implemented. Such reports should be designed to be useful to protocol engineers in selecting algorithms. e.g. number of bytes per signature, single thread computation time, single thread verification time, etc.

The intended outcome is to provide information about algorithms and primitives, along with secure implementations, to help protocol designers achieve post quantum security.

## Process

The pqsg should build implementations of cryptographic constructions that are post quantum secure. This includes things as simple as hash functions and vector commitment schemes, along with more complex structures like arguments of knowledge and asymmetric signature/encryption schemes.

All implementations should be written in Rust and should include support and tests for the following targets:
- aarch64-*-*
- armv7-*-*
- x86_64-*-*
- wasm32-unknown-unknown

Wasm implementations _may_ include javascript bindings.

Tests should be written from the perspective of an external consumer. That is, implementation details should be abstracted as much as possible leaving only inputs and outputs.

Implementations of specific functions should be reviewed by cryptographers and engineers during development. This should form a bottom up guarantee of security. e.g. reviewers sign off on low level functions, then are able to sign off on higher level functions that consume lower level functions that have previously been reviewed. Approvals should be noted in comments near the source implementation and should include the name of each reviewer, and the commit hash that was reviewed.

## Primitives and algorithms

Prospective primitives and algorithms that may be implemented:
- [More Efficient Commitments from Structured Lattice Assumptions](https://eprint.iacr.org/2016/997.pdf)
- [Efficient Zero-Knowledge Proofs for Commitments from Learning With Errors over Rings](https://eprint.iacr.org/2014/889.pdf)

