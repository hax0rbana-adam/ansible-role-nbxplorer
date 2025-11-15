A simple role to build & install NBXplorer on Debian.

# Dependencies

This role depends on having the .NET core SDK installed. You can accomplish
that any way you like, but I'd suggest the `hax0rbana_adam.dotnetcore_sdk` role.
To install that role:

```
ansible-galaxy role install hax0rbana_adam.dotnetcore_sdk
```

You will have to add that to your playbook to install version 8 of the SDK
before calling this role.

There's also a dependency on the `community.postgres` collection. This can not
be documented in `meta/main.yml` because Ansible doesn't allow roles to depend
on collections. As such, the best we can do is to document it here. To install
that collection, run:

```sh
ansible-galaxy collection install community.postgresql
```

This role has tasks that will use that role. There's no need to add anything
to your playbook for postgres after the community collection is installed.

# Variables

See defaults/main.yml for the variables and an explanation as to what they do.

# Examples
## Playbook
Here's an example of a playbook to install NBXplorer on the local machine. It does
not require you have SSH running.

```yaml
- hosts: localhost
  connection: local
  become: true
  roles:
    - role: hax0rbana_adam.nbxplorer
      nbxplorer_db_pass: hunter2
      nbxplorer_rpc_cookie: rpcauth=bitcoin:4713e4cd89109157dea224c825455d05$b678b6e99f062c1e4bc321c5b75a9f08ece59177391c79a1de3d99d2a9321fed
```

To make a playbook to run this role on a remote host:

```yaml
- hosts: all
  remote_user: root
  roles:
    - role: hax0rbana_adam.nbxplorer
      nbxplorer_db_pass: hunter2
```

# Official repo location
All activity takes place on the official GitLab instance:
[https://gitlab.hax0rbana.org/public-repos/ansible/ansible-role-nbxplorer](https://gitlab.hax0rbana.org/public-repos/ansible/ansible-role-nbxplorer)

Any other hosting providers, such as GitHub.com and GitLab.com, are just mirrors
and we do not monitor the issue trackers over there.

# Support
## Matrix channel
You can also join our Matrix channel: #ansible:hax0rbana.org

This is a good place to ask questions or make requests without having to sign
up for another account.

# Contributing
See [contributor guidelines](CONTRIBUTING.md).

# License
This project is licensed under MIT License. See [LICENSE](LICENSE) for more details.
