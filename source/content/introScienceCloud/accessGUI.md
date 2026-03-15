{% if slide %}
## Creating a VM via the Web GUI

```{admonition} <i class="fa-solid fa-display"></i> Hands-on
:class: warning
Everyone clicks through the creation of a VM together.
```

### Steps

::::{grid} 1 1 2 2
:gutter: 2

:::{grid-item-card} 1. Launch Instance
- Navigate to **Compute → Instances → Launch Instance**
- Choose a **name**
- Pick a **boot source** (image: `ubuntu-jammy-22.04`)
- Select a **flavor** (e.g. `1cpu-4ram-hpcv3`)
- Set **disk size** and check **block storage** options for the "home" disk
:::

:::{grid-item-card} 2. Network & Security
- Assign to an existing **network** (e.g. `uzh-only`)
- Configure **Network Ports** (e.g., leave them empty for now)
- Configure **Security Group** (e.g., `default` which opens port 22 for SSH)
- Add your **SSH key pair**: 
   - Upload your `~/.ssh/mysecret.pub`
   - Key Pair Name: e.g. `mysecret`
   - Key Type: `SSH Key`
:::

:::{grid-item-card} 3. Connect
**SSH access:**
```bash
ssh ubuntu@<floating-ip>
```

**Web console:**
Use the built-in **Console** tab in the GUI for direct terminal access.
:::

:::{grid-item-card} 4. Cleanup
- **Stop** the VM when not in use
- **Delete** the instance when done
- Verify that **block storage volumes** persist independently
:::
::::

:::{admonition} Block Storage Persistence
:class: tip
When you delete a VM, attached block storage volumes remain.
They can be re-attached to a new instance later.
:::

{% endif %}
