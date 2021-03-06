========================
Team and repository tags
========================

.. image:: http://governance.openstack.org/badges/openstack-ansible-os_cloudkitty.svg
    :target: http://governance.openstack.org/reference/tags/index.html

.. Change things from this point on

OpenStack-Ansible CloudKitty
############################
:tags: openstack, cloudkitty, cloud, ansible
:category: \*nix

This Ansible role installs and configures OpenStack cloudkitty.

This role will install the following Upstart services:
    * cloudkitty-api
    * cloudkitty-processor

Required Variables
==================

.. code-block:: yaml

    cloudkitty_service_password
    cloudkitty_rabbitmq_password
    cloudkitty_container_mysql_password
    cloudkitty_galera_address

Example Playbook
================

.. code-block:: yaml

    - name: Install cloudkitty server
      hosts: cloudkitty_all
      user: root
      roles:
        - { role: "os_cloudkitty", tags: [ "os-cloudkitty" ] }
      vars:
        external_lb_vip_address: 172.16.24.1
        internal_lb_vip_address: 192.168.0.1
        cloudkitty_galera_address: "{{ internal_lb_vip_address }}"
        cloudkitty_container_mysql_password: "SuperSecretePassword1"
        cloudkitty_service_password: "SuperSecretePassword2"
        cloudkitty_rabbitmq_password: "SuperSecretePassword3"
