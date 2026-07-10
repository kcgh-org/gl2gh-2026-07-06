## 2. Requirements

### 2.1 Operating System Requirements

| Requirement | Description | Manual GEI Migration | GitHub Actions (GHA) Pipeline Migration |
|------------|-------------|----------------------|------------------------------------------|
| Operating System | Supported operating system used for migration execution. | Ubuntu. | GitHub-hosted runner (`ubuntu-latest`) or a self-hosted runner running Ubuntu. |

### 2.2 Software Requirements

| Requirement | Description | Manual GEI Migration | GitHub Actions (GHA) Pipeline Migration |
|------------|-------------|----------------------|------------------------------------------|
| curl | Used by migration scripts. | Required. | Validated automatically by the workflow. |
| jq | Used for JSON processing within migration scripts. | Required. | Validated automatically by the workflow. |
| git | Required for repository operations. | Required. | Validated automatically by the workflow. |
| docker | Required for running gl-exporter and generating migration archives. | Required. | Validated automatically by the workflow. |
| node | Required for migration JavaScript utilities. | Node.js v20 or later. | Validated automatically by the workflow. |
| npm | Required for dependency management. | npm v10 or later. | Validated automatically by the workflow. |
| GitHub CLI (`gh`) | Required for migration, monitoring, and mannequin commands. | Required. | Validated automatically by the workflow. |

### 2.3 Required Token Scopes

#### GitLab API Token

- Must be generated using an administrator account.
- Requires full API access.
- Used for:
  - Inventory generation
  - Migration archive generation using gl-exporter

#### GitHub Personal Access Token (PAT)

Required scopes:

- repo
- admin:org
- workflow
- user

### 2.4 GitHub Access Requirements

| Manual GEI Migration | GitHub Actions (GHA) Pipeline Migration |
|----------------------|------------------------------------------|
| Access to migration scripts and target GitHub organizations. | Access to migration scripts, workflow execution, workflow artifacts, GitHub environments, approvals, and migration monitoring. |

### 2.5 Intermediate Storage for Migration Archives

Supported storage options:

| Storage Type | Supported Capacity |
|-------------|-------------------|
| GitHub Storage | Up to 30 GB |
| Azure Storage | Up to 40 GB |
| AWS Storage | Up to 40 GB |

