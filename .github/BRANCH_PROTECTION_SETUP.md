# Branch Protection Configuration Guide

This guide provides step-by-step instructions for configuring branch protection on the `main` branch of this repository.

## Overview

Branch protection ensures that:
- No direct pushes to `main` (all changes must go through pull requests)
- Pull requests require at least 1 approval before merging
- CI checks must pass before merging
- Force pushes and branch deletion are prevented

## Prerequisites

Before configuring branch protection, ensure:
1. ✅ GitHub Actions workflows are in place (see `.github/workflows/ci.yml`)
2. ✅ At least one PR has been merged to populate available status checks
3. ✅ You have admin access to the repository

## Configuration Steps

### 1. Navigate to Branch Protection Settings

1. Go to the repository: [matkowsky/form-direction-architecture-torah](https://github.com/matkowsky/form-direction-architecture-torah)
2. Click the **Settings** tab at the top
3. In the left sidebar, click **Branches**
4. Under **Branch protection rules**, click **Add branch protection rule**

### 2. Target the Main Branch

5. In the **Branch name pattern** field, enter: `main`

### 3. Configure Pull Request Requirements

6. Under **Protect matching branches**, enable the following:

   ✅ **Require a pull request before merging**
   - This forces all changes to go through the PR process
   
   Then configure these sub-options:
   
   ✅ **Require approvals**
   - Set the number of required approvals to: **1**
   
   ✅ **Dismiss stale pull request approvals when new commits are pushed** (Recommended)
   - This ensures that new changes are reviewed
   
   ✅ **Require review from Code Owners** (Optional)
   - Enable this if you want to use the `.github/CODEOWNERS` file
   - This ensures that designated code owners must approve changes

### 4. Require Status Checks to Pass

7. Enable: ✅ **Require status checks to pass before merging**

   After enabling, you'll see a list of available checks. Select the following:
   
   - ✅ **build** - Overall build check
   - ✅ **markdown-lint** - Markdown linting validation
   - ✅ **link-check** - Link validation
   - ✅ **validate-structure** - Repository structure validation
   
   Additional recommended option:
   
   ✅ **Require branches to be up to date before merging** (Recommended)
   - This ensures the PR branch has the latest changes from `main`
   - Forces a rebase/merge before merging, ensuring CI runs on the final state

   **Note**: If you don't see the checks listed yet, you need to:
   1. Merge this PR first to run CI
   2. Return to branch protection settings
   3. Select the checks that appear

### 5. Prevent Force Pushes and Deletions

8. Configure these security settings:

   ❌ **Allow force pushes** → Leave **UNCHECKED**
   - Prevents rewriting history on `main`
   
   ❌ **Allow deletions** → Leave **UNCHECKED**
   - Prevents accidental deletion of the `main` branch

### 6. Optional: Restrict Push Access

9. (Optional) ✅ **Restrict who can push to matching branches**
   - Click to enable
   - Add specific users, teams, or GitHub Apps that can push
   - Leave empty to restrict all direct pushes (recommended for PR-only workflow)
   - You can add automation/release bots if needed

### 7. Additional Recommended Settings

Consider enabling these optional protections:

- ✅ **Require linear history** (Optional)
  - Prevents merge commits, requires rebasing
  - Keeps history cleaner but requires team familiarity with rebasing

- ✅ **Include administrators** (Recommended)
  - Applies these rules even to repository administrators
  - Ensures consistent workflow for all contributors

- ✅ **Require conversation resolution before merging** (Recommended)
  - Ensures all review comments are addressed before merge

### 8. Save the Configuration

10. Click **Create** (or **Save changes** if editing an existing rule) at the bottom

## Verification

After configuration, verify the protection is working:

1. Try to push directly to `main` - it should be rejected
2. Create a test PR and verify:
   - You cannot merge without approval
   - You cannot merge with failing CI
   - The merge button is disabled until requirements are met

## Workflow After Configuration

Once branch protection is active, the workflow is:

1. Create a feature branch from `main`
2. Make changes and push to the feature branch
3. Open a pull request to `main`
4. CI checks run automatically
5. Request review from team member
6. Address any review comments
7. Once approved and CI passes, merge the PR
8. Delete the feature branch (optional but recommended)

## Troubleshooting

### Status checks not appearing
- Merge at least one PR that triggers the CI workflow
- Wait a few minutes and refresh the branch protection settings page

### Cannot merge even with approval
- Check that all required status checks are passing
- Ensure the branch is up to date with `main` if that option is enabled

### Need to bypass protection (emergency)
- Repository admins can temporarily disable the rule
- After emergency fix, re-enable protection immediately
- Document why bypass was needed

## Related Files

- `.github/workflows/ci.yml` - CI workflow configuration
- `.github/CODEOWNERS` - Code ownership definitions

## Additional Resources

- [GitHub Branch Protection Documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [CODEOWNERS Documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)
