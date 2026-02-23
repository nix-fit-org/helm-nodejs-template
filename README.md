# nodejs-app-template

![Version: 1.3.0](https://img.shields.io/badge/Version-1.3.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

## Description

Node.js app chart template

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Ivan Chizh | <wizardy.oni@gmail.com> | <https://github.com/drone117> |
| Dmitrii Bogomolnyi | <nex1gen@yandex.ru> | <https://github.com/nex1gen> |

## Values

Example values.yaml

```yaml
---

gateway:
  enabled: true
  httpRoute:
    host: nodejs-app.host

app:
  env:
    ENV_1: VALUE_1
    ENV_2: VALUE_2
  secrets:
    env:
      SECRET_ENV_1: SECRET_VALUE_1
      SECRET_ENV_2: SECRET_VALUE_2
```

```yaml
---

ingress:
  enabled: true
  host: nodejs-app.host

app:
  env:
    ENV_1: VALUE_1
    ENV_2: VALUE_2
  secrets:
    env:
      SECRET_ENV_1: SECRET_VALUE_1
      SECRET_ENV_2: SECRET_VALUE_2
```

## Contribute

Don't forget to generate every time actual README.md:

```bash
helm-docs --template-files=README.md.gotmpl
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| annotations.deployment.prometheus.path | string | `"/metrics"` | prometheus metrics path |
| annotations.deployment.prometheus.port | string | `"3000"` | prometheus metrics port |
| annotations.deployment.prometheus.scrape | string | `"true"` | prometheus scrape enabled |
| annotations.ingress.certManager.clusterIssuer | string | `"letsencrypt-prod"` | cert manager cluster issuer |
| app.env | string | `nil` | app environment variables |
| app.secrets.env | string | `nil` | app secret environment variables |
| gateway.enabled | bool | `false` | gateway enabled |
| gateway.httpRoute.filters.responseHeaderModifier.set | list | `[{"name":"Content-Security-Policy","value":"frame-src 'self'; frame-ancestors 'self'; object-src 'none';"},{"name":"Referrer-Policy","value":"no-referrer"},{"name":"Strict-Transport-Security","value":"max-age=31536000; includeSubDomains"},{"name":"X-Content-Type-Options","value":"nosniff"},{"name":"X-Frame-Options","value":"SAMEORIGIN"}]` | response header modifier filter set (override headers values) |
| gateway.httpRoute.host | string | `""` | httproute hostname |
| gateway.httpRoute.httpSectionName | string | `"http-80"` | httproute gateway parentRef |
| gateway.name | string | `"envoy-gateway"` | gateway object name |
| gateway.namespace | string | `"envoy-gateway-system"` | gateway object namespace |
| image.digest | string | `nil` | image digest |
| image.pullPolicy | string | `"Always"` | image pull policy |
| image.registry | string | `"nix-docker.registry.twcstorage.ru"` | image registry |
| image.repository | string | `nil` | image repository |
| image.tag | string | `nil` | image tag |
| ingress.className | string | `"nginx"` | ingress class name |
| ingress.enabled | bool | `false` | open access to app outside cluster via ingress |
| ingress.host | string | `""` | ingress host |
| ingress.tlsSecretName | string | `""` | ingress tls secret name (where to store signed certificate from Let's Encrypt) |
| podDisruptionBudget.maxUnavailable | int | `1` | pod disruption budget max unavailable |
| probes.liveness.failureThreshold | int | `5` | liveness probe max consecutive failures before restart |
| probes.liveness.initialDelaySeconds | int | `60` | liveness probe initial delay |
| probes.liveness.path | string | `"/"` | liveness probe path |
| probes.liveness.periodSeconds | int | `5` | liveness probe period |
| probes.liveness.timeoutSeconds | int | `1` | liveness probe timeout per attempt |
| probes.readiness.failureThreshold | int | `5` | readiness probe max consecutive failures before unready |
| probes.readiness.initialDelaySeconds | int | `60` | readiness probe inital delay |
| probes.readiness.path | string | `"/"` | readiness probe path |
| probes.readiness.periodSeconds | int | `5` | readiness probe period |
| probes.readiness.timeoutSeconds | int | `1` | readiness probe timeout per attempt |
| progressDeadlineSeconds | int | `180` | progress deadline seconds |
| replicaCount | int | `2` | replica count |
| resources.limits.cpu | string | `"500m"` | cpu limits |
| resources.limits.ephemeral-storage | string | `"256Mi"` | ephemeral storage limits |
| resources.limits.memory | string | `"768Mi"` |  |
| resources.requests.cpu | string | `"250m"` | cpu requests |
| resources.requests.ephemeral-storage | string | `"128Mi"` | ephemeral storage requests |
| resources.requests.memory | string | `"256Mi"` | memory requests |
| revisionHistoryLimit | int | `1` | revision history limit |
| service.port | int | `3000` | service port (app) |
| serviceAccount.automountServiceAccountToken | bool | `false` | service account auto mount token |
| serviceAccount.name | string | `"default"` | service account name |
| updateStrategy.rollingUpdate.maxSurge | int | `1` |  |
| updateStrategy.rollingUpdate.maxUnavailable | int | `1` |  |
| updateStrategy.type | string | `"RollingUpdate"` | update strategy type |
