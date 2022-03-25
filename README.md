# Latest Release Version
Action for getting latest release's **`tag name`** of a repository
# Usage
```yaml
- name: Get latest release's tag_name of `actions/runner` using action
  id: get-version-action
  uses: fangqiuming/latest-release-version@v1
  with:
    repository: actions/runner
    token: ${{ secrets.GITHUB }}
- name: A/B Check
    if: steps.get-version-action.outputs.tag_name != 'v2.289.1'
    uses: actions/github-script@v3
    with:
      script: |
        core.setFailed("${{ steps.get-version-action.outputs.tag_name }} \
        and v2.289.1 are not equivalent!')
```
## Inputs
| Input Name  | Description                                                       | Default Value              |
|-------------|-------------------------------------------------------------------|----------------------------|
| repository  | Repository name with owner. For example, `actions/runner`         | `${{ github.repository }}` |
| token       | [`Personal access token (PAT)`][PAT] used to read the repository  | `${{ github.token }}`      |

[PAT]: https://help.github.com/en/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets

## Output
| Output Name | Description                                                                                    |
|-------------|------------------------------------------------------------------------------------------------|
| tag_name    | Tag name of the `repository`'s latest release. For example, `v2.289.1`                         |
