## Example repository for deploying preview environments on Koyeb

This repository houses a simple application used to demonstrate how to automatically deploy preview environments on Koyeb based on pull request branches.

The repository defines two workflows: `deploy-previews.yaml` and `cleanup-previews.yaml`.

The `deploy-previews.yaml` file is automatically triggered whenever a pull request is opened, updated, or re-opened.  It deploys the pull request branch to Koyeb so that you can test and validate the changes in a realistic deployment environment.

The `cleanup-preveiws.yaml` file is automatically triggered whenever a pull request is merged or closed.  It tears down the preview environment running on Koyeb since it is no longer necessary.

## Using this repository

To use this repository, first [generate a Koyeb personal access token](https://app.koyeb.com/user/settings/api).

Next, on GitHub, fork this repository into your own account.  In your fork, click the repository's **Settings** tab, choose select **Secrets and variables** and then **Actions**.  Click **New repository secret** to add a new secret.

Fill in the secret creation form with the following:

* **Name:** `KOYEB_API_TOKEN` (must match the secret value from the workflow files)
* **Value:** The Koyeb personal access token you generated as the secret value.

Your fork should now be configured to deploy to your Koyeb account automatically whenever a pull request is made against the `main` branch.  Once the pull request is closed or merged, the preview environment will be automatically stopped.
