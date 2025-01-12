# Testing Directory

## File Directory
- `/infrastructure`: Testing infrastructure
- `/suites`: [Tekton](https://tekton.dev/) CRDs defining test suites

## Testing Infrastructure Design Choices
Testing infrastructure will be divided up into three layers: Management Cluster, Test Orchestration, and Clusters Under Test. The Management Cluster will be a Kubernetes cluster with configured add-ons to run a Test Orchestration tool that will create Clusters Under Test where Karpenter will be tested.
- `Management Cluster`: An EKS Cluster with configured Add-ons and Tekton
- `Test Orchestration`: Tekton to create Clusters Under Test and run Test Suites.
- `Clusters Under Test`: Rapid iteration [KIT](https://github.com/awslabs/kubernetes-iteration-toolkit) Guest Clusters and EKS Clusters where test suites will run.

*Note: A more formal design discussing testing infrastructure will come soon.*

## Developing
Use the Tekton UI to manage and monitor resources and test-runs:
```
kubectl port-forward service/tekton-dashboard -n tekton-pipelines 9097&
open http://localhost:9097
```
