<p align="center">
  <img width="250px" src="https://user-images.githubusercontent.com/13738772/201432652-63a10fc1-a6a5-423f-8ee0-b18a11308077.svg" />
<p align="center">


## Neon Branch Management Workflow 🚀
This GitHub action:
- creates Neon branches for new, reopened, and updated PRs
- resets Neon branches based on the `Reset Neon Branch` label
- deletes Neon branches for closed or merged PRs

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
    secrets:
      NEON_API_KEY: ${{ secrets.NEON_API_KEY }}
```

The full list of supported parameters can be viewed in the [_neon-preview-branches-for-pull-requests.yml_](/.github/workflows/neon-preview-branches-for-pull-requests.yml) file.

## How to set up a Neon API key

1. Navigate to the **Account settings** page in the Neon console. Select **API keys** > **Create new API key**.
2. Add your Neon API key to your GitHub Secrets:
  1. In your GitHub repository, go to **Project settings** and locate **Secrets** at the bottom of the left sidebar.
  2. Click **Actions** > **New Repository Secret**.
  3. Name the secret **NEON_API_KEY** and paste your API key in the **Secret** field
  4. Click **Add Secret**.

**IMPORTANT**: Do not share your Neon API key or expose it in your actions or code.
