## Fetching a Container at Runtime

{% if slide %}
**Dynamic Remote Retrieval:**
* Container images hosted on OCI-compliant registries (e.g., GitHub Container Registry - GHCR) can be retrieved dynamically upon execution.
* **Access Control:** The retrieval process necessitates either public image visibility or explicit host authentication.

**Authentication (Private Registries):**
```bash
export APPTAINER_DOCKER_USERNAME=<github_username>
export APPTAINER_DOCKER_PASSWORD=<personal_access_token>

```

**Execution via ORAS URI:**

```bash
apptainer run oras://ghcr.io/pscicomp/env-sif:latest

```

{% endif %}

{% if page %}
Upon publication to a remote container registry, such as the GitHub Container Registry (GHCR), an Apptainer image can be retrieved dynamically at the precise moment of runtime initiation. This architectural pattern eliminates the necessity of manually distributing massive static image files (`.sif`) across diverse compute nodes prior to task execution.

### Access and Authentication

For dynamic retrieval to function successfully, the host runtime environment must possess the appropriate access rights to the target repository. This is managed through two primary mechanisms:

1. **Public Visibility:** The package housing the container image is configured to be publicly accessible. It is important to note that repository visibility is often decoupled from package visibility. For instance, on GitHub, the container package settings must be explicitly modified to allow public read access (typically managed via the interface at `https://github.com/orgs/<organization>/packages/container/<image_name>/settings`).
2. **Explicit Authentication:** If the container registry is restricted (private), authentication credentials must be injected into the host environment prior to invoking the Apptainer command. Apptainer parses standard Docker registry authentication variables for this purpose. A Personal Access Token (PAT) configured with the requisite `read:packages` permissions is strictly required.

```bash
# Export standard authentication credentials for private registry access
export APPTAINER_DOCKER_USERNAME=<github_username>
export APPTAINER_DOCKER_PASSWORD=<personal_access_token>

```

### Execution via ORAS

Once the access configuration is resolved, the container is invoked directly by referencing the ORAS (OCI Registry As Storage) protocol URI. Apptainer automatically pulls the image into the local host cache (defaulting to `~/.apptainer/cache`), converts it to the native SIF format if necessary, and executes the default runscript.

```bash
# Execute the remote container directly via the OCI registry
apptainer run oras://ghcr.io/pscicomp/env-sif:latest

```

```{admonition} Caching Behavior
:class: note
Subsequent executions invoking the identical URI and tag will systematically leverage the locally cached image. This minimizes network overhead and significantly reduces startup latency, provided the remote image digest has not mutated.

```

{% endif %}
