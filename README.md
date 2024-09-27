# `introspect` GitHub Action

The `introspect` action retrieves metadata from a GitHub workflow run and provides it as JSON output. It can also extract the SHA of a specified reusable workflow from the run metadata.

## Key Features

- **Workflow Metadata:** Fetches detailed information about the current workflow run.
- **Reusable Workflow SHA:** Extracts the SHA of a referenced reusable workflow.

## How to Use

To add this action to your workflow, include the following steps in your GitHub Actions YAML file:

```yaml
- name: Get workflow metadata
  id: introspection
  uses: kobo-labs/introspect@<version>
  with:
    github_token: ${{ secrets.GITHUB_TOKEN }}
    referenced_workflow: "<owner>/<repo>/.github/workflows/<reusable_workflow>.yml"

- name: Output reusable workflow SHA
  run: |
    echo "Referenced Workflow SHA: ${{ steps.introspection.outputs.referenced_workflow_sha }}"
```

### Inputs

- **`github_token`** (required): Your GitHub token for authentication.
- **`referenced_workflow`** (required): The path to the reusable workflow, formatted as `<owner>/<repo>/.github/workflows/<reusable_workflow>.yml`.

### Outputs

- **`referenced_workflow_sha`**: The SHA of the specified reusable workflow.
