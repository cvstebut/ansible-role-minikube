Role Name
=========

This Ansible creates a minikube profile (cluster) on a Windows host with the hyperv driver. It will insure that the latest version of minikube is installed on the target using the chocolatey module.

The role will install the minikube cluster and fetch the generated KUBECONFIG file from the default location on the windows host (%HOMEPATH%/.kube/config). %HOMEPATH% is the home directory of the user used to connect to the windows host. The fetched file will then be stored on the Ansible controller (localhost) and can be utilized for further configuration.

Requirements
------------

The python openshift is needed by the k8s modules.

### Install openshift python module

```console
pip3 install openshift
```

Role Variables
--------------
See `./vars/main.yml`

```yaml
kubeconfig_folder: /home/ansible/.ci/kubeconfig
minikube_dry_run: false
minikube_embed_certs: true
minikube_profile: minikube04
minikube_cpus: 3   # 
minikube_memory: "5g"  # b k m g
minikube_disk_size: "25000mb"
minikube_driver: hyperv
minikube_hyperv_virtual_switch: internalLAN
```

Dependencies
------------

### chocolatey.chocolatey

```console
ansible-galaxy collection install chocolatey.chocolatey
```

### community.kubernetes

```console
ansible-galaxy collection install community.kubernetes
```


Example Playbook
----------------

```yaml
---
- hosts: cvs004
  roles:
    - ansible-role-minikube
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).


