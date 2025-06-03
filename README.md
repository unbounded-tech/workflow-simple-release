# workflow-simple-release

Workflow to publish a simple github release.

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
      tag_name: ${{ github.ref_name }}
      release_name: ${{ github.ref_name }}
      draft: false
      prerelease: false
```
