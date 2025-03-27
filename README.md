# `vet` - Policy Driven OSS Component Vetting

Gitlab CI component for [vet](https://github.com/safedep/vet). It allows policy
driven vetting of OSS components against supply chain security risks.

## Usage

```yaml
include:
  - component: gitlab.com/safedep/ci-components/vet/scan@<VERSION>
```

#### Using Inputs

```yaml
include:
  - component: gitlab.com/safedep/ci-components/vet/scan@<VERSION>
    inputs:
      cloud: true
      cloud-key: $CLOUD_KEY
      cloud-tenant: $CLOUD_TENANT
      artifact-access: 'all'
```

where `<VERSION>` is the latest released tag or `main`.

## Configuration Options

The GitLab CI component accepts the following inputs:

### `vet scan`

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `policy` | string |  | Path to policy file, default policy will be used when not given |
| `version` | string | latest | Version of vet to use |
| `cloud` | boolean | `false` | Synchronize configuration, policy and report with SafeDep cloud |
| `cloud-key` | string | | API key to use for synchronizing report with SafeDep cloud |
| `cloud-tenant` | string | | Tenant ID to use for synchronizing report with SafeDep cloud |
| `exception-file` | string | | Path to exception file |
| `trusted-registries` | array | `[]` | List of trusted registry base URLs |
| `timeout` | number | `300` | Timeout in seconds for vet to wait for external service results to be available. For malicious package analysis, this set the maximum time to wait for the analysis results to be available |

## CI Configuration

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `stage` | string | `test` | The stage where you want the job to be added |
| `artifact-access` | string | `developer` | Determines who can access the job artifacts from the GitLab UI or API. Options: `all`, `developer`, `none` |
| `allow-failure` | boolean | `true` | Whether the scanning job is allowed to fail |
