Kubernetes documentation: https://kubernetes.io/docs/home/

kubectl commands: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands

Use the `grep` function to filter output e.g. command `| grep readOnly`

## GET

List all pods in the default namespace: `kubectl get pods`

List all pods in the default namespace with more information: `kubectl get pods -o wide`

List all pods in all namespaces: `kubectl get pods -A`

List all pods in a specific namespace (e.g. alpha): `kubectl -n alpha get pods`

List a specific pod (e.g. nginx) in YAML format: `kubectl get pod nginx -o yaml`

Save the YAML definition of a specific pod in a file: `kubectl get pod nginx -o yaml > webserver.yaml`

## DELETE

Delete a pod: `kubectl delete pod nginx`

Delete a pod (faster, not recommended in production): `kubectl delete pod nginx --force`

## DESCRIBE

Describe a pod (e.g. nginx): `kubectl describe pod nginx`

## EXEC

Exec into a pod and check the user running that pod: `kubectl exec nginx -- whoami`

## EDIT

Edit the pod to modify its configuration: `kubectl edit pod nginx`

## AUDIT

Reference: https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/

Reference for apiserver audit log settings: https://kubernetes.io/docs/tasks/debug/debug-cluster/audit/#log-backend

Check if audit is enabled: `cat /etc/kubernetes/manifests/kube-apiserver.yaml | grep audit`

A good practice is to backup the original yaml before edit: `cp kube-apiserver.yaml kube-apiserver-backup.yaml`

Edit kube-apiserver: `vi /etc/kubernetes/manifests/kube-apiserver.yaml`

## USERS & GROUPS

Check UID of root: `id root` or `cat /etc/passwd | grep root`

Setup a new password for user1: `passwd user1`

Delete an user: `userdel user1`

Delete a group: `groupdel group1`

Suspend an user and prevent the suer to login: `usermod -s /usr/sbin/nologin user1`

Add a user with home directory (home/user1), bash login, part of admin group and uid 2328:
`useradd -d /home/user1 -s /bin/bash -G admin -u 2328 user1`

## SYSTEM HARDENING

Check installed packages on Ubuntu: `apt list --installed`

Show install kernel modules: `lsmod`

List all service units files: `systemctl list-units --all`

Stop a service (e.g: nginx): `systemctl stop nginx.service`

Find the location of the service: `systemctl status nginx.service`

Remove the service: `rm /lib/systemd/system/nginx.service`

Deny a kernel module (e.g: evbug): `vi /etc/modprobe.d/blacklist.conf`

Remove a specific package (e.g.: nginx): `apt remove nginx -y`

Identify the service listening on specific port (e.g: 9090): `netstat -natp | grep 9090`

Kill/stop the service to free the port (e.g: apache2): `systemctl stop apache2`

Install latest version available in repos for a specific service (e.g: wget): `apt install wget -y`

## SECCOMP

Useful programs: strace, tracee
Seccomp profile default location: /var/lib/kubelet/seccomp

Trace syscalls for a specific command (e.g ls): `strace -o outputfile ls`

## RUNTIME

Check what is the runtime used (docker, crio or others): `kubectl get nodes -o wide`

Check the default runtime in Docker: `docker info | grep Runtime`

Check the runtime classes: `kubectl describe runtimeclasses`

## SSH

Passing the private key while connecting to a server: `ssh -i`


