kubectl commands: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands

List all pods in the default namespace: `kubectl get pods`

List all pods in the default namespace with more information: `kubectl get pods -o wide`

List all pods in all namespaces: `kubectl get pods -A`

List all pods in a specific namespace (e.g. alpha): `kubectl -n alpha get pods`

List a specific pod (e.g. webserver) in YAML format: `kubectl get pod webserver -o yaml`



