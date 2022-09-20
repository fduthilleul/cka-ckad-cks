kubectl commands: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands

Use the `grep` function to filter output e.g. command `| grep readOnly`

## GET

List all pods in the default namespace: `kubectl get pods`

List all pods in the default namespace with more information: `kubectl get pods -o wide`

List all pods in all namespaces: `kubectl get pods -A`

List all pods in a specific namespace (e.g. alpha): `kubectl -n alpha get pods`

List a specific pod (e.g. webserver) in YAML format: `kubectl get pod webserver -o yaml`

Save the YAML definition of a specific pod in a file: `kubectl get pod webserver -o yaml > webserver.yaml`

## AUDIT

Reference: https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/

Check if audit is enabled: `cat /etc/kubernetes/manifests/kube-apiserver.yaml | grep audit`

Reference for apiserver audit log settings: https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/#log-backend

A good practice is to backup the original yaml before edit: `cp kube-apiserver.yaml kube-apiserver-backup.yaml`

Edit kube-apiserver: `vi /etc/kubernetes/manifests/kube-apiserver.yaml`
