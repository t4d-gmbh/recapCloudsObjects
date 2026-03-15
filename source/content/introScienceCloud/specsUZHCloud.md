{% if slide %}
## UZH Science Cloud — Overview

```{admonition} <i class="fa-solid fa-circle-info"></i> Full documentation
:class: margin tip
[docs.s3it.uzh.ch/cloud2](https://docs.s3it.uzh.ch/cloud2/overview/)
```

:::::{grid} 1 1 2 2
:gutter: 3

::::{grid-item-card} <i class="fa-solid fa-cubes"></i> Capacity
:class-header: sd-bg-primary sd-bg-text-light

OpenStack-based IaaS

^^^

- Managed by **S3IT** (UZH)
- OpenStack cloud OS
- **~3 000 vCPUs** / **~20 TB RAM** / **~100 GPUs**
- Multiple **flavors** (VM sizes) available

+++
<i class="fa-solid fa-link"></i> [Cloud Overview](https://docs.s3it.uzh.ch/cloud2/overview/)
::::

::::{grid-item-card} <i class="fa-solid fa-coins"></i> Approximate Yearly Costs
:class-header: sd-bg-info sd-bg-text-light

Two example configurations

^^^

| Config | Specs | ~CHF/year |
|---|---|---|
| **Standard** | 4 vCPU, 16 GB RAM, 100 GB | ~500 |
| **GPU** | 8 vCPU, 32 GB RAM, 1 GPU, 100 GB | ~3 000 |

Costs are approximate and depend on the specific flavor and allocation model.

::::
:::::

---

### Access & Services

- **SSH** via UZH VPN to your VM (e.g. `ssh ubuntu@<floating-ip>`)
- **Web GUI**: [cloud.s3it.uzh.ch](https://cloud.s3it.uzh.ch)
- **CLI**: `openstack` Python client
- Services include: **Compute (Nova)**, **Block Storage (Cinder)**, **Object Storage (Swift)**, **Networking (Neutron)**

:::{admonition} Object Storage
:class: note
The Science Cloud also provides **Swift Object Storage** as a service — we will look at this next.
:::

{% endif %}
