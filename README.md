# vet - Policy Driven OSS Component Vetting

[![Go Report Card](https://goreportcard.com/badge/github.com/safedep/vet)](https://goreportcard.com/report/github.com/safedep/vet)
[![GoDoc](https://godoc.org/github.com/safedep/vet?status.svg)](https://godoc.org/github.com/safedep/vet)
![License](https://img.shields.io/github/license/safedep/vet)
![Release](https://img.shields.io/github/v/release/safedep/vet)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/safedep/vet/badge)](https://api.securityscorecards.dev/projects/github.com/safedep/vet)


Gitlab CI component for [vet](https://github.com/safedep/vet). It allows policy
driven vetting of OSS components against supply chain security risks.

## Usage

```yaml
include:
  - component: gitlab.com/safedep/ci-components/vet/scan@<VERSION>
    inputs:
      policy: '.gitlab/vet/policy.yml'
```

where `<VERSION>` is the latest released tag or `main`.


## Configuration Options

The GitLab CI component accepts the following inputs:

### Vet-Specific Inputs

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `policy` | string | `.gitlab/vet/policy.yml` | Path to policy file, default policy will be used when not given |
| `cloud` | boolean | `false` | Synchronize configuration, policy and report with SafeDep cloud |
| `cloud-key` | string | | API key to use for synchronizing report with SafeDep cloud |
| `cloud-tenant` | string | | Tenant ID to use for synchronizing report with SafeDep cloud |
| `version` | string | `latest` | vet version to use for the scan. Defaults to using latest release |
| `exception-file` | string | | Path to exception file |
| `trusted-registries` | array | `[]` | Comma separated list of trusted registry base URLs |
| `timeout` | number | `300` | Timeout in seconds for vet to wait for external service results to be available. For malicious package analysis, this set the maximum time to wait for the analysis results to be available |

### GitLab-Specific Inputs

| Input | Type | Default | Description |
|-------|------|---------|-------------|
| `stage` | string | `test` | The stage where you want the job to be added |
| `artifact_access` | string | `developer` | Determines who can access the job artifacts from the GitLab UI or API. Options: `all`, `developer`, `none` |
| `allow_failure` | boolean | `true` | Whether the scanning job is allowed to fail |
