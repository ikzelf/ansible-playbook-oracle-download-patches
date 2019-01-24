Ansible Playbook: oracle-download-patches
=========================================

Download patches from My Oracle Support directly to the server.

This playbook uses [getMOSPatch.sh](https://github.com/MarisElsins/TOOLS/blob/master/Shell/getMOSPatch.sh) script, by Maris Elsins.


Supported OS:
-------------
* RedHat
* CentOS
* OracleLinux

Requirements
------------

This playbook requires the `oracle` and `oracle-download-patches` roles.

`$ ansible-galaxy install -r roles/requirements.yml`

Examples
--------

    $ ansible-playbook playbook.yml --list-tasks
    $ ansible-playbook playbook.yml --list-tags

Download patches enlisted in `oracle_download_patches_list` variable. The playbook prompts for MOS credentials, both user and password.

    $ ansible-playbook playbook.yml

Download patches. The playbook prompts for MOS password only, username provided in `--extra-vars`.

    $ ansible-playbook playbook.yml --extra-vars='{"oracle_download_patches_mos_user": "user@foo.com"}'

Download patches provided explicitly in `--extra-vars` (overwrites `oracle_download_patches_list` variable).

    $ ansible-playbook playbook.yml --extra-vars='{oracle_download_patches_list: [ 28689165, 28689148 ]}'

Download patches provided explicitly (here: opatch). Use regular expression to filter the filenames (here: only 11.2 opatches selected to download).

    $ ansible-playbook playbook.yml --extra-vars='{oracle_download_patches_list: [ 6880880 ], oracle_download_patches_regexp: ".112."}'

Specify the target directory path for the downloaded patches.

    $ ansible-playbook playbook.yml --extra-vars='{ oracle_download_patches_stage_directory: /some/directory/opatch }'


License
-------

GPLv3 - GNU General Public License v3.0

Author Information
------------------

This playbook was created in 2018 by [Krzysztof Lewandowski](mailto:Krzysztof.Lewandowski@fastmail.fm).

