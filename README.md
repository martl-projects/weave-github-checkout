# GitHub checkout

Fetches release files from GitHub for you, with what a project's GitHub releases service grants you, or with your
own GitHub access where it leaves that to you. Each file is checked against what its maintainer released.

It's a fetcher: a client app of yours, not a project's. Weave runs it on your node when you install something a
GitHub releases service hands out, in the projects you added it for (or all of them). It reaches GitHub's API and
its file store (`api.github.com`, `*.githubusercontent.com`) only. Your token, if you give it one, stays sealed on
your node.

    weave fetcher add github-checkout --projects <project>
    weave fetcher set github-checkout --setting GITHUB_TOKEN=…

## Where it lives

This repository is its only source. Weave ships it by pinning one of its releases (Weave's
`packages/shipped/pinned.json`: this repository, a tag and the archive's SHA-256), so what Weave ships is exactly
the file released here. A new version: tag it here, then move the pin in Weave.

## Building and releasing

```
npm install
npm run build              # → github-checkout.wasm
```

A tag `v*` builds it on GitHub and attaches `weave-github-checkout.tar.gz` (the component, `weave.app.json` and this README) to a
release (`.github/workflows/release.yml`).

`wit/service.wit` is Weave's service interface (`packages/sdk/wit` in Weave's repository), copied here to build against.
