# Contributing to Funora

Thank you for considering a contribution. This document is the organization-wide baseline;
individual repositories may add their own rules on top of it.

> **The project is in design.** Most repositories have no code yet. The most useful
> contributions right now are protocol observations, fixtures and specification review —
> not implementation.

## Language

The project is developed in **English**. This is not a preference, it is a constraint:
several parts cannot be translated after the fact without a breaking change.

**English only, no exceptions:**

- identifiers in code, namespaces, package names,
- specification: entity IDs, event type IDs, enum values, capability keys, error codes,
- exception messages emitted by the framework,
- branch names, commit titles, pull request titles, issue labels,
- `CHANGELOG`, migration notes, RFCs, conformance suites and fixtures,
- file and directory names.

**Russian is welcome** in: issue and discussion bodies, the `protocol-breakage` form, and the
Russian sections of user-facing documentation. If you are more comfortable writing an issue
in Russian, do that — it is better than an unclear issue in English.

Error message text is **not** part of the public contract: `code` and `params` are stable,
the human-readable `message` is an English hint that may change at any time. Do not match on
it.

## Before you open a pull request

Open an issue first, unless the change is a typo or a documentation fix. For anything that
changes the public API, the protocol layer, event ordering, authentication or the plugin
model, expect to write an RFC first — these are expensive to reverse once packages are
published.

## Branches and commits

Work happens on short-lived branches off `main`. `main` is always releasable.

```
feat/1234-market-snapshot
fix/221-chat-parser-empty-message
perf/311-event-dispatch-index
docs/155-python-quickstart
ci/91-pypi-trusted-publish
```

Pull request titles follow Conventional Commits: `feat:`, `fix:`, `perf:`, `docs:`,
`refactor:`, `test:`, `build:`, `ci:`, `chore:`. Pull requests are squash-merged, so a clean
commit history inside the branch is not required.

## Code origin

Funora is an independent reimplementation based on observed protocol behaviour. Prior art has
been reviewed, but **no source code is copied** from other FunPay projects — including
identifiers, selector strings, regular expressions, message texts and module structure.

Two of the projects commonly referenced in this space carry **no license at all**, which
means no permission to copy has been granted. One is GPL-3.0, which is incompatible with our
Apache-2.0 licensing. By opening a pull request you confirm that your contribution is your
own work or is compatible with Apache-2.0, and that you have not copied code from a source
that does not permit it.

This applies equally to AI-assisted contributions. If you used an assistant, you are still
the one asserting the above.

## What will not be accepted

- CAPTCHA bypass, anti-detection, browser fingerprint spoofing.
- Proxy rotation intended to evade rate limits or bans.
- Mass messaging, broadcast helpers, or anything that makes spam convenient. FunPay's
  published rules prohibit this explicitly — clause 1.9 at
  [funpay.com/trade/info](https://funpay.com/trade/info) — and it puts users at risk.
- Automatic generation of reviews or ratings.
- Anything that stores or transmits a session key in plain text by default.

## Security

Do not report vulnerabilities in a public issue, and never paste a session key, raw
signed-in HTML, or private chat contents anywhere public. See
[SECURITY.md](SECURITY.md).
