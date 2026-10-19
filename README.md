# Tecnots Shared CI/CD Workflows

Reusable GitHub Actions workflows that run on the Tecnots self-hosted Azure runners
(`azure-linux-eastasia-01-*`, labels: `self-hosted, linux, azure, eastasia`).

## Callable workflows

| Workflow | Description |
|---|---|
| `.github/workflows/deploy-api.yml` | Build .NET API Docker image, push to ACR, deploy to Azure App Service |

## Usage (from 360Solve/360Solve-ERP)

```yaml
jobs:
  deploy:
    uses: Tecnots/.github/.github/workflows/deploy-api.yml@main
    with:
      ref: v2.23.0
      environment: staging
      app-name: 360solve-api-staging
      resource-group: rg-360solve-staging
      full-image: crtecnots.azurecr.io/360solve-api:abc1234
      env-latest-tag: crtecnots.azurecr.io/360solve-api:staging-latest
    secrets:
      CALLER_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
