# Microshift management and automation Collection

[![OpenSSF Best Practices](https://bestpractices.coreinfrastructure.org/projects/7481/badge)](https://bestpractices.coreinfrastructure.org/projects/7481)

[Ansible Collection](https://docs.ansible.com/ansible/latest/user_guide/collections_using.html)
for management and automation of [microshift](https://microshift.io/)
to build [rpm-ostree](https://rpm-ostree.readthedocs.io/en/latest/) based images to run microshift,
configure microshift, upgrade microshift, deploy [kubernetes](https://kubernetes.io/) workloads on
microshift, and much more. 

## Installing

To install this collection and its dependencies, you will need to use the [Ansible](https://github.com/ansible/ansible) `ansible-galaxy` command:

```shell
ansible-galaxy collection install git+https://github.com/redhat-cop/edge.microshift
```

## Development Environment

To use this while developing, run the following commands from within your local directory you pulled to this git repo to in order to symlink this git repo to the appropriate [Ansible Collection path](https://docs.ansible.com/ansible/latest/reference_appendices/config.html#collections-paths).

```shell
  mkdir -p ~/.ansible/collections/ansible_collections/edge
  ln -s $(pwd) ~/.ansible/collections/ansible_collections/edge/microshift 
```

## How to use
You will need a RHEL 8.7 system
### RPM based install
The RHEL 8.7 system will act as the microshift node.
Run the playbook to install microshift on the RHEL system:
```bash
ansible-playbook playbook/microshift_rpm_install.yml
```

### RPM-Ostree based install
The RHEL 8.7 system will act as the image build server to create the Microshift image.
Run the playbook to create an image with the microshift package and configurations on the RHEL system:
```bash
ansible-playbook playbook/microshift_image_build.yml
```

### Deploy application
To deploy an application on a running microshift system refer to the app role [README](https://github.com/redhat-cop/edge.microshift/blob/main/roles/app/README.md)


## Communication

<!--List available communication channels. In addition to channels specific to your collection, we also recommend to use the following ones.-->

We announce releases and important changes through Ansible's [The Bullhorn newsletter](https://github.com/ansible/community/wiki/News#the-bullhorn). Be sure you are [subscribed](https://eepurl.com/gZmiEP).

Join us in the `#devel:ansible.com` (general use questions and support), `#community:ansible.com` (community and collection development questions), and other [Matrix channels](https://docs.ansible.com/ansible/devel/community/communication.html#ansible-community-on-matrix).

We take part in the global quarterly [Ansible Contributor Summit](https://github.com/ansible/community/wiki/Contributor-Summit) virtually or in-person. Track [The Bullhorn newsletter](https://eepurl.com/gZmiEP) and join us.

For more information about communication, refer to the [Ansible Communication guide](https://docs.ansible.com/ansible/devel/community/communication.html).


## Governance

<!--Describe how the collection is governed. Here can be the following text:-->

The process of decision making in this collection is based on discussing and finding consensus among participants.

Every voice is important. If you have something on your mind, create an issue or dedicated discussion and let's discuss it!


## Supported Versions of Ansible

<!--start requires_ansible-->

## Ansible version compatibility

This collection has been tested against following Ansible versions: **>=2.12**.

Plugins and modules within a collection may be tested with only specific
Ansible versions.  A collection may contain metadata that identifies these versions.
PEP440 is the schema used to describe the versions of Ansible.

<!--end requires_ansible-->

## Tested with Ansible

<!-- List the versions of Ansible the collection has been tested with. Must match what is in galaxy.yml. -->

- ansible-core (devel)
- ansible-core 2.14 (stable)
- ansible-core 2.13 (stable)
- ansible-core 2.12 (stable)

## Included content

<!-- Galaxy will eventually list the module docs within the UI, but until that is ready, you may need to either describe your plugins etc here, or point to an external docsite to cover that information. -->
Roles:
- image_builder
- app
- rpm_install

## Using this collection

<!--Include some quick examples that cover the most common use cases for your collection content. It can include the following examples of installation and upgrade (change edge.microshift correspondingly):-->

### Installing the Collection from Ansible Galaxy

**NOTE: This collection is not yet in Ansible Galaxy as it is under heavy development and has not been released**

Before using this collection, you need to install it with the Ansible Galaxy command-line tool:
```bash
ansible-galaxy collection install edge.microshift
```

You can also include it in a `requirements.yml` file and install it with `ansible-galaxy collection install -r requirements.yml`, using the format:
```yaml
---
collections:
  - name: edge.microshift
```

Note that if you install the collection from Ansible Galaxy, it will not be upgraded automatically when you upgrade the `ansible` package. To upgrade the collection to the latest available version, run the following command:
```bash
ansible-galaxy collection install edge.microshift --upgrade
```

You can also install a specific version of the collection, for example, if you need to downgrade when something is broken in the latest version (please report an issue in this repository). Use the following syntax to install version `0.1.0`:

```bash
ansible-galaxy collection install edge.microshift:==0.1.0
```

See [Ansible Using collections](https://docs.ansible.com/ansible/devel/user_guide/collections_using.html) for more details.

## Code of Conduct

We follow the [Ansible Code of Conduct](https://docs.ansible.com/ansible/devel/community/code_of_conduct.html) in all our interactions within this project.

If you encounter abusive behavior, please refer to the [policy violations](https://docs.ansible.com/ansible/devel/community/code_of_conduct.html#policy-violations) section of the Code for information on how to raise a complaint.

## Contributing to this collection

<!--Describe how the community can contribute to your collection. At a minimum, fill up and include the CONTRIBUTING.md file containing how and where users can create issues to report problems or request features for this collection. List contribution requirements, including preferred workflows and necessary testing, so you can benefit from community PRs. If you are following general Ansible contributor guidelines, you can link to - [Ansible Community Guide](https://docs.ansible.com/ansible/devel/community/index.html). List the current maintainers (contributors with write or higher access to the repository). The following can be included:-->

The content of this collection is made by people like you, a community of individuals collaborating on making the world better through developing automation software.

We are actively accepting new contributors.

Any kind of contribution is very welcome.

You don't know how to start? Refer to our [contribution guide](https://docs.ansible.com/ansible/devel/community/contributor_path.html)!

We use the following guidelines:

* [CONTRIBUTING](https://docs.ansible.com/ansible/devel/community/contributor_path.html#making-your-first-contribution)
* [REVIEW_CHECKLIST](https://docs.ansible.com/ansible/devel/community/collection_contributors/collection_reviewing.html)
* [Ansible Community Guide](https://docs.ansible.com/ansible/latest/community/index.html)
* [Ansible Development Guide](https://docs.ansible.com/ansible/devel/dev_guide/index.html)
* [Ansible Collection Development Guide](https://docs.ansible.com/ansible/devel/dev_guide/developing_collections.html#contributing-to-collections)

## Collection maintenance

The current maintainers are listed in the [MAINTAINERS](MAINTAINERS) file. If you have questions or need help, feel free to mention them in the proposals.

To learn how to maintain / become a maintainer of this collection, refer to the [Maintainer guidelines](https://docs.ansible.com/ansible/devel/community/maintainers.html).

See [Ansible Using collections](https://docs.ansible.com/ansible/devel/user_guide/collections_using.html) for more details.

## Release notes

See the [changelog](https://github.com/redhat-cop/edge.microshift/blob/main/changelogs/changelog.yaml).

## More information

<!-- List out where the user can find additional information, such as working group meeting times, slack/IRC channels, or documentation for the product this collection automates. At a minimum, link to: -->

* [Ansible Collection overview](https://github.com/ansible-collections/overview)
* [Ansible User guide](https://docs.ansible.com/ansible/devel/user_guide/index.html)
* [Ansible Developer guide](https://docs.ansible.com/ansible/devel/dev_guide/index.html)
* [Ansible Collections Checklist](https://github.com/ansible-collections/overview/blob/main/collection_requirements.rst)
* [Ansible Community code of conduct](https://docs.ansible.com/ansible/devel/community/code_of_conduct.html)
* [The Bullhorn (the Ansible Contributor newsletter)](https://us19.campaign-archive.com/home/?u=56d874e027110e35dea0e03c1&id=d6635f5420)
* [News for Maintainers](https://github.com/ansible-collections/news-for-maintainers)

## Licensing

<!-- Include the appropriate license information here and a pointer to the full licensing details. If the collection contains modules migrated from the ansible/ansible repo, you must use the same license that existed in the ansible/ansible repo. See the GNU license example below. -->

GNU General Public License v3.0 or later.

See [LICENSE](https://www.gnu.org/licenses/gpl-3.0.txt) to see the full text.

