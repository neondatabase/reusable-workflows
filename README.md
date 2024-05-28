<p align="center">
  <img width="250px" src="https://user-images.githubusercontent.com/13738772/201432652-63a10fc1-a6a5-423f-8ee0-b18a11308077.svg" />
<p align="center">


## Neon Branch Management Workflow 🚀
This GitHub action:
- creates a new Neon branches for new, reopened, updated PRs
- reset Neon branches based on `Reset Neon Branch` label
- deletes Neon branches for closed PRs

Here is an example of how to use it:

```yml
name: Create/Delete/Reset Branch for Pull Request Workflow
run-name: Create/Delete/Reset Branch for Pull Request Workflow

on:
  pull_request:
    types:
      - opened
      - reopened
      - synchronize
      - closed
      - labeled

jobs:
  neon_branch_management:
    name: Create/Delete/Reset Branch for Pull Request Job
    uses: neondatabase/reusable-workflows/.github/workflows/neon-preview-branches-for-pull-requests.yml@main
    with:
      project_id: proud-salad-35321605
      parent_branch: main
      db: neondb
      role: neondb_owner
    secrets:
      inherit
```

The full list of supported parameters can be seen in the [_neon-preview-branches-for-pull-requests.yml_](/.github/workflows/neon-preview-branches-for-pull-requests.yml) file.

## How to set up the NEON_API_KEY
Navigate to you the Account page on your Neon console. In the Developer Settings, Generate a new API key if you don't have one already.
It's important not to share the API key or expose it in your actions or code. This is why you need to add the API key to a new GitHub secret.

In your GitHub repo, go to `Settings` and locate `Secrets` at the bottom of the left sidebar. Click on `Actions` and then on the `New repository secret` button to create a new secret.
Name the secret `NEON_API_KEY` and paste the API key generated on the Neon console in the `Secret*` field, then press `Add secret` button.
