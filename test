## 2. Requirements

| Requirement | Description | Manual GEI Migration | GitHub Actions (GHA) Pipeline Migration |
|------------|-------------|----------------------|------------------------------------------|
| Operating System | Platform used to execute migration activities. | Ubuntu. | GitHub-hosted runner (`ubuntu-latest`) or a self-hosted runner running Ubuntu. |
| Docker | Required for building and running the `gl-exporter` container used for migration archive generation. | Required. | Required. The workflow validates Docker availability and access automatically. |
| Node.js | Required for executing JavaScript-based migration utilities. | Node.js v20 or later. | Installed automatically if missing and the runner has sudo access. |
| npm | Required for managing JavaScript package dependencies. | npm v10 or later. | Installed automatically if missing and the runner has sudo access. |
| GitHub CLI (`gh`) | Required for inventory generation, migration operations, monitoring, and mannequin management. | Required. | Installed automatically if missing and the runner has sudo access. |
| GitHub CLI Extensions | Required for inventory generation, migration monitoring, and mannequin management. | Install manually. | Installed automatically during workflow execution. |
| GitHub PAT | Used to authenticate migration operations against GitHub. | Required. | Required. Configured as a GitHub Environment secret. |
| GitLab API Token | Used for inventory generation and migration archive creation. | Required. | Required. Configured as a GitHub Environment secret. |
| Inventory File | CSV file containing source and target repository mapping information. | Generated and maintained manually. | Generated manually and provided as workflow input. |
| Intermediate Storage | Temporary storage location used for migration archives. | GitHub, Azure, or AWS. | GitHub, Azure, or AWS. |
| GitHub Object Storage Feature Flag | Required to support GitHub migration archive uploads. | Required. | Required. |
| GitHub Authentication | Authentication of GitHub CLI against the target GitHub environment. | Performed manually using `gh auth login`. | Performed automatically by the workflow using `GH_PAT`. |
| GitHub Environments | Used to store variables, secrets, approvals, and workflow controls. | Not required. | Required. |
| Approval Gates | Controls progression to migration and monitoring stages. | Not applicable. | Configured through GitHub Environment approvals. |
| IP Allow Lists | Network configuration required by customer security policies. | Configure if applicable. | Configure if applicable. |
