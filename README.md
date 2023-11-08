# noobient.pippatch

## Synopsys

This role lets you patch pip packages with a supplied patch file.

## Parameters

| Name | Required | Example | Description |
|---|---|---|---|
| `package` | yes | `ansible-core` | pip package to patch. |
| `patch` | yes | `ansible-core-ssh-fix.patch` | Patch filename in your `templates` directory without the `.j2` suffix. |
| `force` | no | `true` | If `true`, the pip module is installed if missing. |

## Templating

| Name | Example | Description |
|---|---|---|
| `pkg_path` | `/home/bviktor/.local/lib/python3.10/site-packages` | Directory where the pip package is installed. |
| `pkg_ver` | `2.14.1` | pip package version. |

## Examples

```yml
- include_role:
    name: bviktor.pippatch
    vars:
      package: ansible-core
      patch: ansible-core-ssh-fix.patch
```

`ansible-core-ssh-fix.patch.j2`:

```diff
diff -ruN ansible.orig/plugins/connection/ssh.py ansible/plugins/connection/ssh.py
--- ansible.orig/plugins/connection/ssh.py	2022-12-07 00:48:38.377050886 +0100
+++ ansible/plugins/connection/ssh.py	2022-12-07 00:49:20.199204222 +0100
@@ -736,8 +736,8 @@
         if not conn_password:
             self._add_args(
                 b_command, (
-                    b"-o", b"KbdInteractiveAuthentication=no",
-                    b"-o", b"PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey",
+                    b"-o", b"KbdInteractiveAuthentication=yes",
+                    b"-o", b"PreferredAuthentications=gssapi-with-mic,gssapi-keyex,hostbased,publickey,keyboard-interactive",
                     b"-o", b"PasswordAuthentication=no"
                 ),
                 u"ansible_password/ansible_ssh_password not set"
```

## Return Values

N/A

## Support

| Platform | Support | Status |
|---|---|---|
| Linter | ✅ | [![Lint](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/lint.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/lint.yml) |
| AlmaLinux 8 | ❌ | N/A |
| AlmaLinux 9 | ✅ | [![AlmaLinux 9](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/almalinux-9.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/almalinux-9.yml) |
| Fedora 37 | ✅ | [![Fedora 37](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/fedora-37.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/fedora-37.yml) |
| Ubuntu 18.04 | ❌ | N/A |
| Ubuntu 20.04 | ✅ | [![Ubuntu 20.04](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/ubuntu-20.04.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/ubuntu-20.04.yml) |
| Ubuntu 22.04 | ✅ | [![Ubuntu 22.04](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/ubuntu-22.04.yml/badge.svg)](https://github.com/noobient/ansible-galaxy-pippatch/actions/workflows/ubuntu-22.04.yml) |
