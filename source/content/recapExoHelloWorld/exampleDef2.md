# Example `.def` #2
```docker
Bootstrap: docker
From: python:3.13-slim

%files
    src/* /app/src/
    scripts/* /app/scripts/
    config/* /app/config/
    exercises/* /app/exercises/
    pyproject.toml /app/

%post
    apt-get update && \
    apt-get install -y --no-install-recommends curl ca-certificates git && \
    rm -rf /var/lib/apt/lists/*

    curl -LsSf https://astral.sh/uv/install.sh | env UV_INSTALL_DIR="/usr/local/bin" sh

%environment
    # Set project venv path
    export VIRTUAL_ENV="$PWD/.venv"
    export PATH="$PWD/.venv/bin:$PATH"

    export UV_PYTHON_PREFERENCE=only-managed
    export UV_PROJECT_ENVIRONMENT="$PWD/.venv"

%runscript
    if [ $# -eq 0 ]; then
        echo ">>> Syncing Python Environment..."
        if [ -f "pyproject.toml" ]; then
            uv sync
            echo ">>> Success: Environment synced."
        else
            echo ">>> Error: No pyproject.toml found in $PWD."
            exit 1
        fi
        exit 0
    fi
    # If arguments are provided, run them inside container
    exec "$@"
```
