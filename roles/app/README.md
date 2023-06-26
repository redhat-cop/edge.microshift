# edge.microshift.app

This role deploys application onto a system running microshift.

## Requirements

The role requires a system to be running microshift which
the `edge.microshift.image_build` role will automate the creation of.

## Role Variables

### microshift_image_pull_secret

Type: file / string
Required: true

Pull secret allows authentication with the container registries that serve the container images used by the official Red Hat supported MicroShift.

For downloading the pull secret from the Red Hat Hybrid Cloud Console, click [here](https://console.redhat.com/openshift/install/pull-secret)

**Note:** If the pull secret is not on the microshift system then the pull secret will need to be set and defined in the playbook.

Example:
```yaml
microshift_image_pull_secret: "{{ lookup('file', '~/pull-secret.txt') }}"
```

### microshift_app_manifests

Type: complex
Required: true

Application manifest files to be deployed on a microshift system. 

Example:

```yaml
microshift_app_manifests:
  - /path/to/manifest1.yaml
  - /path/to/manifest2.yaml
```

## Variables Exported by the Role

None.

## Dependencies

None.

## Example Playbook

```yaml
---
- name: Deploy application on microshift
  hosts: all
  tasks:
    - name: Deploy application
      vars:
        microshift_image_pull_secret: "{{ lookup('file', '~/pull-secret.txt') }}"
        microshift_app_manifests:
          - /manifests/deployment.yaml
          - /manifests/kustomization.yaml
          - /manifests/namespace.yaml
          - /manifests/route.yaml
          - /manifests/service.yaml
      ansible.builtin.import_role:
        name: edge.microshift.app
```


## License

GPLv3
