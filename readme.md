# bviktor.pippatch

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

## Return Values

N/A

## Support

| Platform | Support | Status |
|---|---|---|
| Linter | ✅ | [![Lint](https://github.com/noobient/ansible-pippatch/actions/workflows/lint.yml/badge.svg)](https://github.com/noobient/ansible-pippatch/actions/workflows/lint.yml) |
| AlmaLinux 8 | ❌ | N/A |
| AlmaLinux 9 | ✅ | [![AlmaLinux 9](https://github.com/noobient/ansible-pippatch/actions/workflows/almalinux-9.yml/badge.svg)](https://github.com/noobient/ansible-pippatch/actions/workflows/almalinux-9.yml) |
| Fedora 37 | ✅ | [![Fedora 37](https://github.com/noobient/ansible-pippatch/actions/workflows/fedora-37.yml/badge.svg)](https://github.com/noobient/ansible-pippatch/actions/workflows/fedora-37.yml) |
| Ubuntu 18.04 | ❌ | N/A |
| Ubuntu 20.04 | ✅ | [![Ubuntu 20.04](https://github.com/noobient/ansible-pippatch/actions/workflows/ubuntu-20.04.yml/badge.svg)](https://github.com/noobient/ansible-pippatch/actions/workflows/ubuntu-20.04.yml) |
| Ubuntu 22.04 | ✅ | [![Ubuntu 22.04](https://github.com/noobient/ansible-pippatch/actions/workflows/ubuntu-22.04.yml/badge.svg)](https://github.com/noobient/ansible-pippatch/actions/workflows/ubuntu-22.04.yml) |
