# Kubernetes Namespaces Simple Backup

This project has as an objective to help you to create a simple backup of the Kubernetes namespaces generating files in yaml format.

The script was made to be simple and functional.
It has a pretty output to help you to see what's happing while the process is running.

The process will run using `kubectl` tool. So you're gonna have to set the right context before of the execution.

> I know that there are many opensource tools to create backups in the whole cluster (not only namespaces but also certs, keys, and more) but the idea of this script is to run a quick process using `kubectl` and not running an Application inside your cluster.

## Prerequisites

All you need is to have [`kubectl`](https://kubernetes.io/docs/tasks/tools/install-kubectl/) installed with the right context configured.

## Confs

There are few variables (below) to adjust if you want to change the default behavior.

```
# Change if you need
DESTINATION_DIR=.
K8S_BACKUP_COMPONENTS=("deployment" "service" "hpa" "serviceaccount" "rolebinding")
```

Theses are quite intuitive but let me explain:

* `DESTINATION_DIR`: Where de backup will be stored;
* `K8S_BACKUP_COMPONENTS`: Components of the Kubernetes which the script is going to backup using `kubectl get COMPONENT`.

> After the backup, the destination dir will have this directory sctructure: `DESTINATION_DIR/CLUSTER_NAME/DATE_LIKE_201812082029/NAMESPACE_NAME/COMPONENT/application.yaml`

## Running the process

There two ways to run the scrip.

1. The first one is just to call the script with no parameters. This is gonna backup all namespaces in the Kubernetes cluster.
2. The second one is when you want to backup only one namespace. So to do this, you'll need to give the namespace name to the script as the first parameter.

E.g.:

```
./ns_backup.sh default
```

![](video/Kubernetes_Backup.m4v)

## Authors

* **Diogo Munhoz Fraga** - [digmunhoz](https://github.com/digmunhoz)