# northstar-legal branch protection (prepared, not applied)

Public repo on GitHub Free. **Do not click Save until Chase confirms.** Do not purchase Pro. Do not change visibility.

CI check name already recorded: `drafts`.

## Exact settings

URL: https://github.com/AmChase12/northstar-legal/settings/branches → **Add branch protection rule** (classic, not a ruleset)

| Field | Value |
| --- | --- |
| Branch name pattern | `main` |
| Require a pull request before merging | **On** |
| Require approvals | **0** (Chase is the only reviewer; the PR is still required) |
| Dismiss stale pull request approvals when new commits are pushed | **On** |
| Require review from Code Owners | **Off** |
| Restrict who can dismiss pull request reviews | **Off** |
| Allow specified actors to bypass required pull requests | **Off** |
| Require status checks to pass before merging | **On** |
| Status checks that are required | `drafts` |
| Require branches to be up to date before merging | **Off** (optional later) |
| Require conversation resolution before merging | **Off** (optional) |
| Require signed commits | **Off** |
| Require linear history | **Off** (keep merge commits available) |
| Require merge queue | **Off** |
| Require deployments to succeed | **Off** |
| Lock branch | **Off** |
| Do not allow bypassing the above settings | **On** |
| Restrict who can push to matching branches | **Off** unless Chase adds a list of `AmChase12` only |
| Allow force pushes | **Off** |
| Allow deletions | **Off** |

Do not enable GitHub Pages from this change. This does not publish `northstardigi.agency`.
