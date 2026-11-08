# northstar-legal branch protection (prepared, not applied)

This repository is **public**, so classic branch protection and rulesets are available on GitHub Free. **No settings were changed.** Chase applies these in the dashboard when ready.

CI job id already recorded: `drafts` (workflow `CI`, pull_request only).

## Exact clicks

1. Open https://github.com/AmChase12/northstar-legal/settings/branches
2. **Add branch protection rule** (classic). Do not create a ruleset unless you prefer rulesets.
3. Branch name pattern: `main`
4. Enable **Require a pull request before merging**
   - Required approvals: **0** if you are the only reviewer; still require the PR
   - **Dismiss stale pull request approvals when new commits are pushed**
5. Enable **Require status checks to pass before merging**
   - Search and add check name: `drafts`
   - Require branches to be up to date: optional
6. **Allow force pushes**: off
7. **Allow deletions**: off
8. Do **not** enable “Allow specified actors to bypass” except yourself
9. Save

Do not require squash. Do not add CODEOWNERS yet.

This does **not** publish GitHub Pages or change `northstardigi.agency`.
