# edge.microshift.app

This role deploys application onto a system running microshift.

## Requirements

The role requires a system to be running microshift which
the `edge.microshift.image_build` role will automate the creation of.

## Role Variables

### microshift_image_pull_secret

Type: file / string
Required: false

Pull secret allows authentication with the container registries that serve the container images used by the official Red Hat supported MicroShift.

For downloading the pull secret from the Red Hat Hybrid Cloud Console, click [here](https://console.redhat.com/openshift/install/pull-secret)

**Note:** If the pull secret is not on the microshift system then the pull secret will need to be set and defined in the playbook.

Example:
```yaml
microshift_image_pull_secret: "{{ lookup('file', '~/pull-secret') }}"
```

### microshift_app_manifests

Type: complex
Required: true

Application manifest files to be deployed on a microshift system. 

Accepts a list of key value pairs. `src` is for the path the file and `name` is what the file is going to be called on the remote system.

Example:

```yaml
microshift_app_manifests:
  - name: deployment
    src: /path/to/deployment.yaml
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
          - src: /manifests/deployment.yaml
          name: deployment
          - src: /manifests/kustomization.yaml
            name: kustomization
          - src: /manifests/namespace.yaml
            name: namespace
          - src: /manifests/route.yaml
            name: route
          - src: /manifests/service.yaml
            name: service
      ansible.builtin.import_role:
        name: edge.microshift.app
```


## License

GPLv3
