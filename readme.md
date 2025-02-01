# Linkwarden Helm Chart

This Helm chart deploys the Linkwarden application on a Kubernetes cluster.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.2.0+

## Installation

1. **Add the Helm repository:**

    ```sh
    helm repo add linkwarden https://soubenz.github.io/linkwarden-helm-chart/
    helm repo update
    ```

2. **Install the chart:**

    ```sh
    helm install my-linkwarden linkwarden/linkwarden
    ```

    Replace `my-linkwarden` with the name you want to give to your Helm release.

## Configuration

The following table lists the configurable parameters of the Linkwarden chart and their default values.

| Parameter                                 | Description                                                                 | Default                                      |
|-------------------------------------------|-----------------------------------------------------------------------------|----------------------------------------------|
| `replicaCount`                            | Number of replicas                                                          | `1`                                           |
| `image.repository`                        | Image repository                                                            | `ghcr.io/linkwarden/linkwarden`              |
| `image.pullPolicy`                        | Image pull policy                                                           | `IfNotPresent`                               |
| `image.tag`                               | Image tag                                                                   | `latest`                                     |
| `postgres.enabled`                        | Enable PostgreSQL                                                           | `true`                                       |
| `postgres.host`                           | PostgreSQL host                                                             | `postgres`                                   |
| `postgres.port`                           | PostgreSQL port                                                             | `5432`                                       |
| `postgres.username`                       | PostgreSQL username                                                         | `postgres`                                   |
| `postgres.password`                       | PostgreSQL password                                                         | `""`                                         |
| `postgres.database`                       | PostgreSQL database                                                         | `postgres`                                   |
| `postgres.external.enabled`               | Enable external PostgreSQL                                                  | `false`                                      |
| `postgres.external.uri`                   | External PostgreSQL URI                                                     | `""`                                         |
| `serviceAccount.create`                   | Specifies whether a service account should be created                       | `true`                                       |
| `serviceAccount.annotations`              | Annotations to add to the service account                                   | `{}`                                         |
| `serviceAccount.name`                     | The name of the service account to use                                      | `""`                                         |
| `podAnnotations`                          | Annotations to add to the pod                                               | `{}`                                         |
| `podSecurityContext`                      | Pod security context                                                        | `{}`                                         |
| `securityContext`                         | Container security context                                                  | `{}`                                         |
| `service.type`                            | Service type                                                                | `ClusterIP`                                  |
| `service.port`                            | Service port                                                                | `80`                                         |
| `ingress.enabled`                         | Enable ingress                                                              | `false`                                      |
| `ingress.className`                       | Ingress class name                                                          | `""`                                         |
| `ingress.annotations`                     | Ingress annotations                                                         | `{}`                                         |
| `ingress.hosts`                           | Ingress hosts                                                               | `[{ host: chart-example.local, paths: [{ path: /, pathType: ImplementationSpecific }] }]` |
| `ingress.tls`                             | Ingress TLS configuration                                                   | `[]`                                         |
| `resources`                               | Resource requests and limits                                                | `{}`                                         |
| `autoscaling.enabled`                     | Enable autoscaling                                                          | `false`                                      |
| `autoscaling.minReplicas`                 | Minimum number of replicas                                                  | `1`                                          |
| `autoscaling.maxReplicas`                 | Maximum number of replicas                                                  | `100`                                        |
| `autoscaling.targetCPUUtilizationPercentage` | Target CPU utilization percentage                                          | `80`                                         |
| `nodeSelector`                            | Node selector                                                               | `{}`                                         |
| `tolerations`                             | Tolerations                                                                 | `[]`                                         |
| `affinity`                                | Affinity                                                                    | `{}`                                         |
| `configuration.paginationTakeCount`       | Pagination take count                                                       | `""`                                         |
| `configuration.storageFolder`             | Storage folder                                                              | `""`                                         |
| `configuration.autoscrollTimeout`         | Autoscroll timeout                                                          | `""`                                         |
| `configuration.publicDisableRegistration` | Disable public registration                                                 | `""`                                         |
| `configuration.publicCredentialsEnabled`  | Enable public credentials                                                    | `""`                                         |
| `configuration.disableNewSSOUsers`        | Disable new SSO users                                                       | `""`                                         |
| `configuration.reArchiveLimit`            | Re-archive limit                                                            | `""`                                         |
| `configuration.maxLinksPerUser`           | Maximum links per user                                                      | `""`                                         |
| `configuration.archiveTakeCount`          | Archive take count                                                          | `""`                                         |
| `configuration.browserTimeout`            | Browser timeout                                                             | `""`                                         |
| `configuration.ignoreUnauthorizedCA`      | Ignore unauthorized CA                                                      | `""`                                         |
| `configuration.ignoreHttpsErrors`         | Ignore HTTPS errors                                                         | `""`                                         |
| `configuration.ignoreUrlSizeLimit`        | Ignore URL size limit                                                       | `""`                                         |
| `configuration.publicDemo`                | Enable public demo                                                          | `""`                                         |
| `configuration.publicDemoUsername`        | Public demo username                                                        | `""`                                         |
| `configuration.publicDemoPassword`        | Public demo password                                                        | `""`                                         |
| `configuration.publicAdmin`               | Public admin                                                                | `""`                                         |
| `configuration.publicMaxFileBuffer`       | Public max file buffer                                                      | `""`                                         |
| `configuration.monolithMaxBuffer`         | Monolith max buffer                                                         | `""`                                         |
| `configuration.monolithCustomOptions`     | Monolith custom options                                                     | `""`                                         |
| `configuration.pdfMaxBuffer`              | PDF max buffer                                                              | `""`                                         |
| `configuration.screenshotMaxBuffer`       | Screenshot max buffer                                                       | `""`                                         |
| `configuration.readabilityMaxBuffer`      | Readability max buffer                                                      | `""`                                         |
| `configuration.previewMaxBuffer`          | Preview max buffer                                                          | `""`                                         |
| `configuration.importLimit`               | Import limit                                                                | `""`                                         |
| `configuration.playwrightLaunchOptionsExecutablePath` | Playwright launch options executable path                                  | `""`                                         |
| `configuration.maxWorkers`                | Maximum workers                                                             | `""`                                         |
| `configuration.disablePreservation`       | Disable preservation                                                        | `""`                                         |
| `configuration.publicRssPollingIntervalMinutes` | Public RSS polling interval minutes                                        | `""`                                         |
| `configuration.rssSubscriptionLimitPerUser` | RSS subscription limit per user                                            | `""`                                         |
| `configuration.sso.enabled`               | Enable SSO                                                                  | `false`                                      |
| `configuration.sso.apple.enabled`         | Enable Apple SSO                                                            | `false`                                      |
| `configuration.sso.apple.clientId`        | Apple SSO client ID                                                         | `""`                                         |
| `configuration.sso.apple.clientSecret`    | Apple SSO client secret                                                     | `""`                                         |
| `configuration.sso.apple.customName`      | Apple SSO custom name                                                       | `""`                                         |
| `configuration.sso.atlassian.enabled`     | Enable Atlassian SSO                                                        | `false`                                      |
| `configuration.sso.atlassian.clientId`    | Atlassian SSO client ID                                                     | `""`                                         |
| `configuration.sso.atlassian.clientSecret`| Atlassian SSO client secret                                                 | `""`                                         |
| `configuration.sso.atlassian.customName`  | Atlassian SSO custom name                                                   | `""`                                         |
| `configuration.sso.atlassian.scope`       | Atlassian SSO scope                                                         | `""`                                         |
| `configuration.sso.auth0.enabled`         | Enable Auth0 SSO                                                            | `false`                                      |
| `configuration.sso.auth0.clientId`        | Auth0 SSO client ID                                                         | `""`                                         |
| `configuration.sso.auth0.clientSecret`    | Auth0 SSO client secret                                                     | `""`                                         |
| `configuration.sso.auth0.customName`      | Auth0 SSO custom name                                                       | `""`                                         |
| `configuration.sso.auth0.issuer`          | Auth0 SSO issuer                                                            | `""`                                         |
| `configuration.sso.authelia.enabled`      | Enable Authelia SSO                                                         | `false`                                      |
| `configuration.sso.authelia.clientId`     | Authelia SSO client ID                                                      | `""`                                         |
| `configuration.sso.authelia.clientSecret` | Authelia SSO client secret                                                  | `""`                                         |
| `configuration.sso.authelia.wellknownUrl` | Authelia SSO well-known URL                                                 | `""`                                         |
| `configuration.sso.authentik.enabled`     | Enable Authentik SSO                                                        | `false`                                      |
| `configuration.sso.authentik.clientId`    | Authentik SSO client ID                                                     | `""`                                         |
| `configuration.sso.authentik.clientSecret`| Authentik SSO client secret                                                 | `""`                                         |
| `configuration.sso.authentik.customName`  | Authentik SSO custom name                                                   | `""`                                         |
| `configuration.sso.authentik.issuer`      | Authentik SSO issuer                                                        | `""`                                         |
| `configuration.sso.azureAdB2C.enabled`    | Enable Azure AD B2C SSO                                                     | `false`                                      |
| `configuration.sso.azureAdB2C.tenantName` | Azure AD B2C tenant name                                                    | `""`                                         |
| `configuration.sso.azureAdB2C.clientId`   | Azure AD B2C client ID                                                      | `""`                                         |
| `configuration.sso.azureAdB2C.clientSecret`| Azure AD B2C client secret                                                  | `""`                                         |
| `configuration.sso.azureAdB2C.primaryUserFlow`| Azure AD B2C primary user flow                                             | `""`                                         |
| `configuration.sso.azureAd.enabled`       | Enable Azure AD SSO                                                         | `false`                                      |
| `configuration.sso.azureAd.clientId`      | Azure AD client ID                                                          | `""`                                         |
| `configuration.sso.azureAd.clientSecret`  | Azure AD client secret                                                      | `""`                                         |
| `configuration.sso.azureAd.tenantId`      | Azure AD tenant ID                                                          | `""`                                         |
| `configuration.sso.battlenet.enabled`     | Enable Battle.net SSO                                                       | `false`                                      |
| `configuration.sso.battlenet.clientId`    | Battle.net client ID                                                        | `""`                                         |
| `configuration.sso.battlenet.clientSecret`| Battle.net client secret                                                    | `""`                                         |
| `configuration.sso.battlenet.customName`  | Battle.net custom name                                                      | `""`                                         |
| `configuration.sso.battlenet.issuer`      | Battle.net issuer                                                           | `""`                                         |
| `configuration.sso.box.enabled`           | Enable Box SSO                                                              | `false`                                      |
| `configuration.sso.box.clientId`          | Box client ID                                                               | `""`                                         |
| `configuration.sso.box.clientSecret`      | Box client secret                                                           | `""`                                         |
| `configuration.sso.box.customName`        | Box custom name                                                             | `""`                                         |
| `configuration.sso.bungie.enabled`        | Enable Bungie SSO                                                           | `false`                                      |
| `configuration.sso.bungie.clientId`       | Bungie client ID                                                            | `""`                                         |
| `configuration.sso.bungie.clientSecret`   | Bungie client secret                                                        | `""`                                         |
| `configuration.sso.bungie.customName`     | Bungie custom name                                                          | `""`                                         |
| `configuration.sso.bungie.apiKey`         | Bungie API key                                                              | `""`                                         |
| `configuration.sso.cognito.enabled`       | Enable Cognito SSO                                                          | `false`                                      |
| `configuration.sso.cognito.clientId`      | Cognito client ID                                                           | `""`                                         |
| `configuration.sso.cognito.clientSecret`  | Cognito client secret                                                       | `""`                                         |
| `configuration.sso.cognito.customName`    | Cognito custom name                                                         | `""`                                         |
| `configuration.sso.cognito.issuer`        | Cognito issuer                                                              | `""`                                         |
| `configuration.sso.coinbase.enabled`      | Enable Coinbase SSO                                                         | `false`                                      |
| `configuration.sso.coinbase.clientId`     | Coinbase client ID
