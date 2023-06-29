====================================================
CHANGE THIS IN changelogs/config.yaml! Release Notes
====================================================

.. contents:: Topics


v1.0.1
======

Minor Changes
-------------

- Replace system roles with community.general
- Update OSBuild dependency from git to Galaxy

v1.0.0
======

Major Changes
-------------

- image_builder - Added ability to configure ovs-kubernetes and crio proxy
- image_builder - add rhsm repo support
- image_builder - added ability to provide pull secrets to kickstart
- image_builder - added app role to deploy manifests onto microshift system
- image_builder - added default firewall option for mandatory microshift rules and ability to create additional port/sources for zones
- image_builder - added rpm_install role to automate the install for microshift on rpm based systems
- image_builder - added storage config to kickstart file
- image_builder - created new image builder role to create image with microshift and necessary bits baked in

Minor Changes
-------------

- image_builder - add playbook to deploy demo app to microshift
- image_builder - add rhsm repo var for rhocp & fast_datapath_for_rhel
- image_builder - content readme updated
- image_builder - create set_fact loop to set fact in a DRY way
- image_builder - relocate rhsm_repos_info management to infra.osbuild
- image_builder - used latest version for osbuild
- image_builder - uses the new updated way of adding kickstart post to osbuild additional_kickstart_post var
- microshift_e2e_test - add microshift test playbook

Bugfixes
--------

- image_builder - change compose_type to builder_compose_type to pass the value to osbuild builder role
- image_builder - fix issue where iso fails to auto install
- image_builder - pass sshkey instead of the file path
- image_builder - update lvms namespace to match the collections namespace
- image_builder - updated microshift_kickstart_post variable to fix issue with omit in kickstart post
