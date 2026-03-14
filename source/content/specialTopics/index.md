# Special Topics


{% if slide %}
<!-- BUILDING THE SLIDES -->
```{toctree}
:maxdepth: 1

./inMemoryStorage
./clusterCommands.md
```

{% else %}
<!-- BUILDING THE PAGES -->

```{include} ./inMemoryStorage.md
```
```{include} ./clusterCommands.md
```

{% endif %}

