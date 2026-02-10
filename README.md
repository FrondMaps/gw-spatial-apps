# GW Spatial Apps

This repository contains the Spatial Apps site under the `apps/` folder and GitHub Actions workflows used to deploy to Development, Test, and Production environments (Azure Static Web Apps).

**Deployment overview**
- **App location:** `apps/` (built files are uploaded directly from this folder)
- **Deployer:** `Azure/static-web-apps-deploy@v1`

**Workflows**
- Development: [.github/workflows/spatial_apps_dev.yml](.github/workflows/spatial_apps_dev.yml#L1)
- Test: [.github/workflows/spatial_apps_tst.yml](.github/workflows/spatial_apps_tst.yml#L1)
- Production: [.github/workflows/spatial_apps_prd.yml](.github/workflows/spatial_apps_prd.yml#L1)

Deployment details

- Dev
  - Trigger: push to the `deploy-dev` branch OR run the workflow manually via Actions and choose the `deploy-to-dev` input.
  - Workflow path: [.github/workflows/spatial_apps_dev.yml](.github/workflows/spatial_apps_dev.yml#L1)
  - Secret used: `SWA_APPS_DEV_TOKEN`
  - App location: `apps/`

- Test
  - Trigger: push to the `deploy-test` branch OR run the workflow manually via Actions and choose the `deploy-to-test` input.
  - Workflow path: [.github/workflows/spatial_apps_tst.yml](.github/workflows/spatial_apps_tst.yml#L1)
  - Secret used: `SWA_APP_TEST_TOKEN`
  - App location: `apps/`

- Prod
  - Intended trigger: manual workflow dispatch from the `main` branch with the `deploy-to-prd` input.
  - Workflow path: [.github/workflows/spatial_apps_prd.yml](.github/workflows/spatial_apps_prd.yml#L1)
  - Secret used: `SWA_APP_PROD_TOKEN`
  - App location: `apps/`


Manual run examples

- GitHub Actions UI: Go to Actions → "Spatial Apps - PROD Deploy" → Run workflow. Choose branch `main` and the correct input value (see note above).


Secrets

Ensure the following repository secrets are configured in Settings → Secrets:

- `SWA_APPS_DEV_TOKEN` — token for the DEV Static Web App
- `SWA_APP_TEST_TOKEN` — token for the TEST Static Web App
- `SWA_APP_PROD_TOKEN` — token for the PROD Static Web App

Web URL

Dev - https://maps-dev.gw.govt.nz/apps/slr
      https://maps-dev.gw.govt.nz/apps/climate-change
  
Tst - https://maps-test.gw.govt.nz/apps/slr
      https://maps-test.gw.govt.nz/apps/climate-change

Prd - https://maps.gw.govt.nz/apps/slr
      https://maps.gw.govt.nz/apps/climate-change

Local testing

This repo is a static site under `apps/`. To preview locally, open `apps/index.html` in a browser or serve the folder with a simple Live server


## Troubleshooting

- If deployments fail, open the failing workflow run in Actions and inspect the job logs.
- Verify repository/organization Secrets are present and up-to-date (Settings → Secrets → Actions).