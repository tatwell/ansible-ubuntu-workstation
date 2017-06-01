GAE Ansible role
=========

Google App Engine Ansible Role.  
Installs Google App Engine local server for Python, Java, PHP or Go (parametrised).

Requirements
------------

No specific requirements.

Role Variables
--------------

## Mandatory variables

None.

## Optional variables

User-configurable defaults:

    # Temporary directory for the role to work in
    gae_temp_dir: '.tmp'

    # Google App Engine SDK version to download and install
    gae_version: "1.9.30"

    # SDK language to install. One of the following: 'python', 'java', 'php', 'go'
    gae_language: "python"

    # Google App Engine SDK installation directory. By default the user's home directory.
    gae_install_dir: "{{ ansible_env.HOME }}"

    # Google App Engine SDK download directories. In case Google changes them.
    gae_download_url_python: "https://storage.googleapis.com/appengine-sdks/featured/google_appengine_{{ gae_version }}.zip"
    gae_download_url_java: "https://storage.googleapis.com/appengine-sdks/featured/appengine-java-sdk-{{ gae_version }}.zip"
    gae_download_url_php: "https://storage.googleapis.com/appengine-sdks/featured/google_appengine_{{ gae_version }}.zip"
    gae_download_url_go: "https://storage.googleapis.com/appengine-sdks/featured/go_appengine_sdk_linux_amd64-{{ gae_version }}.zip"

    # Role action. Provided for future compatibility if this role can also start a local server or deploy.
    gae_action: 'install'
    

Dependencies
------------

None

Example Playbook
----------------

    - hosts: server
      roles:
      - { role: maciejzasada.gae, gae_action: 'install', gae_language: 'python', gae_install_dir: '/home/vagrant' }

License
-------

MIT

Author Information
------------------

Maciej Zasada <hello@maciejzasada.com>
