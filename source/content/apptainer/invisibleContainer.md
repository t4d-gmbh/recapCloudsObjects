# The "Invisible" Container (and its Hidden Cost)

{% if slide %}
**Integration Focus:** `apptainer shell` provides an interactive environment with mapped host directories and containerized dependencies.

```bash
apptainer shell container/env.sif
Apptainer> python script.py

```

*⚠️ **Hidden Cost:** Loss of strict containment. The container inherits host environment variables and home directories (e.g., `~/.local/`), which can compromise reproducibility.*
{% endif %}

{% if page %}
Because Apptainer prioritizes integration, the `apptainer shell` command can be used to drop into an interactive environment. In this state, host directories are perfectly mapped, but software dependencies are provided by the container.

```bash
apptainer shell container/env.sif
# The session remains in the project directory, but uses containerized software
Apptainer> python script.py

```

* **The Hidden Cost:** While incredibly convenient, this integration comes at the cost of strict containment. Because the container inherits the host's environment variables and home directory, the environment is not perfectly isolated. A script might accidentally rely on a hidden file in the host's `~/.local/` folder, which can cause failures when the script is executed by another user in a different environment.
{% endif %}

