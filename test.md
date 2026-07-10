## 2. Requirements

### 2.1 Operating System Requirements

| Requirement | Description | Manual GEI Migration | GitHub Actions (GHA) Pipeline Migration |
|------------|-------------|----------------------|------------------------------------------|
| Operating System | Supported operating system used for migration execution. | Ubuntu. | GitHub-hosted runner (`ubuntu-latest`) or a self-hosted runner running Ubuntu. |

### 2.2 Software Requirements

| Requirement | Description | Manual GEI Migration | GitHub Actions (GHA) Pipeline Migration |
|------------|-------------|----------------------|------------------------------------------|
| curl | Used by migration scripts and API operations. | Required. | Validated automatically by the workflow. Installed automatically if missing and the runner has sudo access. |
| jq | Used for JSON processing within migration scripts. | Required. | Validated automatically by the workflow. Installed automatically if missing and the runner has sudo access. |
| git | Required for repository operations and cloning. | Required. | Validated automatically by the workflow. Installed automatically if missing and the runner has sudo access. |
| Docker | Required for building and running the `gl-exporter` container used for migration archive generation. | Required. | Validated automatically by the workflow. Installed automatically if missing and the runner has sudo access. Docker access is also validated. |
| Node.js | Required for JavaScript-based migration utilities. | Node.js v20 or later. | Validated automatically by the workflow. Installed automatically if missing and the runner has sudo access. |
| npm | Required for package dependency management. | npm v10 or later. | Validated automatically by the workflow. Installed automatically if missing and the runner has sudo access. |
| GitHub CLI (`gh`) | Required for inventory generation, migration operations, monitoring, and mannequin management. | Required. | Validated automatically by the workflow. Installed automatically if missing and the runner has sudo access. |

> **Note:** If the GitHub Actions runner user does not have sudo access, the workflow cannot install missing dependencies automatically and will fail with the required remediation actions. If Docker is installed but the runner user does not have permission to execute Docker commands, the runner user must be added to the Docker group.

### 2.3 GitHub Access Requirements

| Requirement | Manual GEI Migration | GitHub Actions (GHA) Pipeline Migration |
|------------|----------------------|------------------------------------------|
| GitHub Access | Access to migration scripts and target GitHub organizations. | Access to migration scripts, workflow execution, workflow artifacts, GitHub environments, approval environments, migration monitoring, and target GitHub organizations. |

### 2.4 Required Token Scopes

#### GitLab API Token

- Must be generated using an administrator account.
- Requires **full API access**.
- Used for:
  - Inventory generation using `gh-gitlab-stats`
  - Migration archive generation using `gl-exporter`

#### GitHub Personal Access Token (PAT)

Required scopes:

- `repo`
- `admin:org`
- `workflow`
- `user`

### 2.5 Intermediate Storage for Migration Archives

Migration archives are temporarily stored before migration into GitHub.

Supported storage options:

| Storage Type | Supported Capacity |
|-------------|-------------------|
| GitHub Storage | Up to 30 GB |
| Azure Storage | Up to 40 GB |
| AWS Storage | Up to 40 GB |

Additional requirements:

- Azure CLI is required when using Azure Storage.
- AWS CLI is required when using AWS Storage.

### 2.6 GitHub Object Storage Feature Flag

The GitHub Object Storage feature flag must be enabled for:

- The GitHub enterprise/account handle.
- All target GitHub organizations.

### 2.7 Network Configuration

The customer is responsible for configuring any required IP allow lists according to their implementation.

Reference documentation:

```text
https://docs.github.com/en/enterprise-cloud/latest/migrations/ado/managing-access-for-a-migration-from-azure-devops#configuring-ip-allow-lists-for-migrations
```

### 2.8 GitHub Authentication (Manual GEI Migration Only)

#### GitHub Enterprise Cloud

```bash
gh auth login --hostname github.com
```

#### GitHub Enterprise Cloud with Data Residency

```bash
gh auth login --hostname SUBDOMAIN.ghe.com
```

### 2.9 Required GitHub CLI Extensions

Install the following GitHub CLI extensions:

#### gh-gitlab-stats

Used to generate GitLab inventory reports.

```bash
gh extension install https://github.com/mona-actions/gh-gitlab-stats
```

#### gh-migration-monitor

Used to monitor migration status manually.

```bash
gh extension install https://github.com/mona-actions/gh-migration-monitor
```

#### gh-ado2gh

Used for:

- Migration status checks
- Mannequin CSV generation
- Mannequin reclamation
- Migration monitoring

```bash
gh extension install https://github.com/github/gh-ado2gh
```
