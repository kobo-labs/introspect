# introspect

This GitHub Action is designed to fetch metadata about a workflow run from the GitHub API and provide it as JSON output. Additionally, it extracts the SHA of a specified reusable workflow, if available.

## Features

- Fetches and outputs detailed metadata of the current workflow run.
- Extracts the SHA of a specified reusable workflow from the workflow run metadata.

## Usage

To use this action in your workflow, add the following step to your GitHub Actions YAML file:

```yaml
- name: Get workflow reference
  id: introspection
  uses: clamesc/introspect@<version>
  with:
    github_token: ${{ secrets.GITHUB_TOKEN }}
    referenced_workflow: "<owner>/<repo>/.github/workflows/<reusable_workflow>.yml"

- name: Fetch output
  run: |
    echo "${{ steps.introspection.outputs.referenced_workflow_sha }}"
```
