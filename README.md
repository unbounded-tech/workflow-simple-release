# workflow-simple-release

Workflow to publish a simple github release.

External actions and reusable workflows are pinned to full commit SHAs, with
version comments retained for Renovate updates. This repository's own release
uses its local workflow so a tag runs the definition from that same commit.
Pin this reusable workflow to a reviewed commit SHA in consuming repositories.

## Example Usage

```
name: Trigger GitHub Release

on:
  push:
    tags:
      - 'v*'

permissions:
  contents: write

jobs:
  call-release-workflow:
    uses: unbounded-tech/workflow-simple-release/.github/workflows/workflow.yaml@main
    with:
      tag: ${{ github.ref_name }}
      name: ${{ github.ref_name }}
```
