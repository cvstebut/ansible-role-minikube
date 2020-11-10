Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).


Role Development
----------------

### ToDo

- [ ] Install minikube, if necessary
- [ ] Enable setting of `Kube-Proxy.ipvs.strictARP = True`
- [ ] Gather parameters for generating associated kubeconfig file

#### Install minikube, if necessary

Approach: Use `win_chocolatey`, using `state=latest` in order to install, resp. upgrade to the latest version.

#### Enable setting of `Kube-Proxy.ipvs.strictARP = True`

##### Set `strictARP` using `--extra-config` 

Links
- [github minikube - extra config for kube-proxy PR](https://github.com/kubernetes/minikube/pull/6876/commits/f16d9f7515825605c08f002116b9ab1c00ef3d07)

Unfortunately, it does not seem possible to set hierarchical values in the associated ConfigMap (e.g. ipvs:). Thus, it does not seem to be possible to set strictARP via `--extra-config`.

##### Set `strictARP` using sed script
