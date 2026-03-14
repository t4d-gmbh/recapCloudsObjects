## The HPC Cluster

```{figure} ./../_static/slurmCluster.png
:alt: Slurm Cluster Schema
:width: 100%
```

- **Login Nodes**: Gateway for job submissions and environment management
- **Workload Manager (Slurm)**: Schedules jobs onto available resources
- **Compute Nodes**: Where the actual computation runs
- **Shared Storage**: Parallel filesystem mounted on every node
- User access via **SSH**: `ssh user@cluster.example.com`
