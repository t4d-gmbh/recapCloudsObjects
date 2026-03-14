## Basic Cluster Commands



::::{tab-set}
:::{tab-item} Slurm
:::
:::{tab-item} Unix
```
df -hT -x tmpfs -x devtmpfs -x squashfs
```
```
findmnt -J -t ceph,nfs,nfs4 -o TARGET,SOURCE,FSTYPE
```
:::
::::
