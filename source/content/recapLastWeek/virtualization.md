## Virtualization

::::{grid}
:gutter: 3

:::{grid-item}
:columns: 6
:class: sd-m-auto

**Hardware Virtualization (VMs)**

- Hypervisor decouples OS from hardware
- Full guest OS with its own kernel
- Components: Hardware Definition, Virtual Firmware, Disk Image

**OS-Level Virtualization (Containers)**

- Shared kernel, isolated user space
- Components: Layered Image, Manifest, Isolation (Namespaces + Cgroups)

:::
:::{grid-item}
:columns: 6
:class: sd-m-auto

```{image} ./../_static/hypervisor.png
:alt: Hypervisor
:width: 100%
```
:::
::::

---

::::{grid}
:gutter: 3

:::{grid-item}
:columns: 6
:class: sd-m-auto

```{image} ./../_static/vm.png
:alt: VM
:width: 100%
```
:::
:::{grid-item}
:columns: 6
:class: sd-m-auto

```{image} ./../_static/container.png
:alt: Container
:width: 100%
```
:::
::::

```{admonition} Remember the Manifest
:class: tip

The **manifest** declares resource access and what to run.
In Docker, the `Dockerfile` can contain both instructions for the image _and_ the manifest!
```
