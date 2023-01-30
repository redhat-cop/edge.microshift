Role Name
=========

This role automates the setup server and [osbuild](https://www.osbuild.org/) [compose builds](https://www.osbuild.org/guides/user-guide/user-guide.html) using the osbuild backend [Weldr](https://weldr.io/) API with Microshift and necessary dependencies installed.

Requirements
------------

None

Role Variables
--------------

### builder_blueprint_name

Type: string
Required: false

This is the name of the [osbuild blueprint](https://www.osbuild.org/guides/blueprint-reference/blueprint-reference.html?highlight=distro#distribution-selection-with-blueprints)
to use. The blueprint will be auto generated based on the contents of the 
`builder_compose_customizations` role variable. In the event an of an [rpm-ostree](https://rpm-ostree.readthedocs.io/en/stable/)
based compose type specified by the `builder_compose_type` role variable, the
blueprint name defined in this variable will use used to define the resulting [ostree](https://ostreedev.github.io/ostree/)
repository.

### builder_blueprint_src_path

Type: string
Required: false

This is the path to a location on the osbuild server that the generated
blueprint should be stored at and used as the source content for the osbuild
compose build.

### compose_type

Type: string
Required: false

This variable defines the type of compose desired, valid inputs will vary based
on operating system (RHEL, CentOS Stream, or Fedora) and release version therin.

For RHEL, the Red Hat Enterprise Linux Documentation Team publishes these and they can be found [here](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/composing_a_customized_rhel_system_image/index#composer-output-formats_composer-description).

For CentOS Stream and Fedora, you will need to reference the output of the 
`composer-cli compose types` command on the osbuild server (this can also be 
done on RHEL if preferred).

### pubkey_file

Type: string
Required: false

Path to location of ssh public key to inject into the resulting image to allow
key-based ssh functionality without extra configuration for systems installed
with the resulting build media.

Example:
```yaml
builder_pub_key: ~/.ssh/id_rsa.pub
```


### builder_compose_customizations:

Type: dict
Required: false

This variable is the YAML dict expression of 
[osbuild blueprint](https://www.osbuild.org/guides/blueprint-reference/blueprint-reference.html) customizations.

Example:
```yaml
builder_compose_customizations:
  user:
    name: "testuser"
    description: "test user"
    password: "testpassword"
    key: "{{ builder_pub_key }}"
    groups: '["users", "wheel"]'
  kernel:
    append: "nomst=force"
  services:
    enabled: ["firewalld"]
  firewalld.services:
    enabled: ["ssh", "https"]
    
```

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    ---
    - name: Run microshift image builder role
      become: true
      hosts: all
      gather_facts: true
      tasks:
        - name: Create image with microshift
          ansible.builtin.import_role:
            name: edge.microshift.image_builder

License
-------

GPLv3
