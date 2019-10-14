# Ansible role archive
A role to generate archives

## Requirements
- Hosts should be bootstrapped for ansible usage (have python,...)

## Role Variables

| Variable | Description | Default value |
|----------|-------------|---------------|
| `archive_directories` | Definitions for generating the archives. See below for details. | [] |


### `archive_directories` details

This list contains the definitions for all archives to build

| Variable | Description | Required | Default |
|----------|-------------|----------|---------|
| `path` | The | yes | / |
| `dest` | The target filepath that the archive should be saved to | yes | / |
| `format` | The generating format | no | gz |
| `remove` | Flag to remove the source files after the artifact has been generated. | no | [] |
| `excludes` | List of files and directories to exclude from artifact | no |  [] |


## Dependencies

--

## Example playbook
```yaml
- name: Create archive
  hosts: archive
  roles:
    - role: archive
      vars:
        archive_directories:
          - path: /var/www/repo
            dest: /tmp/archives/archive.tgz
            format: gz
            remove: false
            excludes:
              - scripts/
              - tests/
              - .gitignore
```
