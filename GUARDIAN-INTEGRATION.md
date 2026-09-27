# Guardian integration candidate

Upstream: FileBrowser Quantum (`gtsteffaniak/filebrowser`). Source pin: `e13f7075dc28c7f6bdc586b847591c675202e291` (v2.0.9 source line). License: Apache-2.0. GitHub Actions are disabled on the new fork. No runtime is installed.

## Why this base

The Go backend and Vue interface already provide multi-source browsing, drag/drop operations, search and scoped user access. These are useful implementation foundations; they are not a complete SharePoint replacement. The original File Browser project is archived. This fork must retain the upstream license and track security changes rather than becoming an unmaintained snapshot.

The pinned changelog includes the v2.0.8 fixes for signing-key persistence/fail-closed token validation and upload replacement restrictions, plus the v2.0.9 token migration correction. The advisory inventory still needs an independent source and behavioral review. Do not deploy the older v1.5.6 stable binary merely because the releases API calls it latest stable.

## Integration boundary

- Present the real file listing, selection, search and detail views within Guardian's Storage section.
- Use one owning Guardian lifecycle. Avoid a separately installed anonymous file-server daemon.
- Keep the source/index service read-only until per-root capability and operation tests pass.
- Replace immediate drag/drop mutations with Guardian's authenticated preview/execute contract. Show destination, size certainty, conflicts, permissions and verification progress.
- Bind hosts and volume UUIDs; reject changed or unavailable roots, traversal, symlink escape and stale hashes. No write access to arbitrary paths supplied by the browser.
- Disable public/anonymous shares, media/document previews, external editors and generic token creation until their separate reviewed requirements exist. Keep private content out of cloud prompts and public repository changes.
- Use owner-scoped NAS paths and preserve effective Synology ACLs. Do not claim role isolation based only on folder names or a shared OS login.
- Retain receipts and recoverability across interrupted copies and source retirement. No source deletion before verification and the applicable retention policy.
- Stream measured catalog/resource events with explicit freshness and offline states; do not use UI animations as evidence of live collection.

## Current build result

A bounded, offline upstream authentication test was attempted with automatic toolchain/dependency downloads disabled. It stopped before tests ran: this source requires Go 1.27.0, while the local compiler is Go 1.26.2. No test pass, compiled application, installed identity or secure runtime is claimed.

Before building: admit the exact repository/branch/base and worker routes through the current dispatcher; provide an approved isolated toolchain; verify dependency lockfiles and licenses; run focused security tests, frontend behavior tests and synthetic operation journeys. Only then produce a reviewed package and perform installed Guardian acceptance. No private storage is connected as a shortcut to demonstrating visuals.
