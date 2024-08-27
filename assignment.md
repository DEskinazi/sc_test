# Debug Operations in Kubernetes

Although Kubernetes' self-healing capabilities are built in, failures still occur and issues with deploying, executing, or managing applications in a Kubernetes (k8s) cluster can be challenging. Applications that aren't behaving as expected or are crashing require careful debugging. Fortunately, k8s provides a command line tool, kubectl, which communicates with the Kubernetes API. Kubectl is equipped with several commands you can use to understand, isolate, and remedy common issues you might encounter. Whether the issue is with pods crashing or failing to start, inability to pull an image, networking, resource limitations, or other problems with deployment, you can use kubectl commands to troubleshoot your application.

This article includes:

[Prerequisites](prerequisites)
[Kubectl CLI Syntax](kubectl-cli-syntax)
[Common kubectl Troubleshooting Commands](basic-kubectl-troubleshooting-commands)
[Possible Debug Questions](possible-debug-questions)


## Prerequisites
- Basic [Kubernetes](https://kubernetes.io/docs/concepts/overview/#why-you-need-kubernetes-and-what-can-it-do) knowledge
- [kubectl CLI](https://kubernetes.io/docs/tasks/tools/#kubectl) installed
- Kubernetes [cluster](https://docs.spectrocloud.com/getting-started/deploy-k8s-cluster/) or managed service. Learn about [services offered in Palette](https://docs.spectrocloud.com/devx/services/).

## Kubectl CLI Syntax

The following syntax is used to initiate commands in kubectl.

```shell
kubectl [command]  [TYPE]  [NAME]  [flags]
```

| parameter | description |
| -- | -- |
| `command` | The specified action you want to perform, such as `get`, `describe`, or `logs`.|
| `TYPE` | Indicates the resource type, such as a pod or service. |
| `NAME` | Name of the specified resource. |
| `flags` | Optional flags used to customize the specified command. |

## Common kubectl Troubleshooting Commands

The following list of commands equips you with the most basic tools you need to debug k8s issues.

| command  | description |
| --------------- | -- |
|`kubectl get` | Displays information about specified resources in the current namespace such as pods, nodes, and services. <br> <br> You may need to include the namespace when calling this command. <br> **For example:** `kubectl get pods --namespace` |
|`kubectl describe` | Displays detailed descriptions about specified resources or groups of resources. Applies to pods, services, deployments or nodes. <br> <br> **For example:** `kubectl describe pod <pod-name>`|
|`kubectl exec` | Executes a command in a container. |
|`kubectl logs` | Displays the logs for the specified container in a pod. Use this command to monitor pod behavior, view errors, or verify execution. |
| `kubectl auth can i ...` | Confirms authorization or access to specified resource. |
| `kubectl get events` | Displays recents events.
| `kubectl port-forward` |Allows you to direct services to the port specified. <br><br> **For example:** `kubectl port-forward <pod-name> <local port>:<remote port>` |


## Possible Debug Questions

Troubleshooting issues with your Kubernetes cluster involves some basic methods of investigation such as displaying resources, showing details of those resources, and reviewing logs within a designated namespace.

The following is a list of questions you might ask with a `ImagePullBackOff` error:

- Are the pods visible?
- Are events operating as expected?
- Is the image name spelled correctly?
- Does the image exist?
- Does the image require permissions?
- Is the app accessible?
- Can the app be viewed locally/publicly?

For guidance in using the CLI, review [Access Cluster with CLI](https://docs.spectrocloud.com/clusters/cluster-management/palette-webctl/#access-cluster-with-cli). To learn more about kubectl pod commands, refer to the [Kubernetes](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get) documentation.

## Resources

- [Troubleshooting](https://docs.spectrocloud.com/troubleshooting/)
