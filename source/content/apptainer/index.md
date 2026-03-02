# Apptainer


{% if slide %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./dockerVS
./hpcContext
./systemPackages.md
./invisibleContainer.md
./clusterExo1
```

{% else %}
<!-- BUILDING THE PAGES -->

```{include} ./dockerVS.md
```
```{include} ./hpcContext.md
```
```{include} ./systemPackages.md
```
```{include} ./invisibleContainer.md
```

{% endif %}

