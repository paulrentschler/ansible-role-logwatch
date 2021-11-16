paulrentschler.logwatch
=======================

[![MIT licensed][mit-badge]][mit-link]

Installation and configuration of LogWatch on Ubuntu Linux.


Requirements
------------

None.


Role Variables
--------------

The following variables are available with defaults defined in `defaults/main.yml`:

Set the email address that LogWatch sends the reports to.

    logwatch_mail_to: "root@localhost"

Set the email address for the "From" header in the email that LogWatch sends.

    logwatch_mail_from: '"LogWatch ({{ inventory_hostname }})" <root@localhost>'

Set the group that should get permissions on configuration files.

    logwatch_admin_group: root

Set the level of detail in the Logwatch report. This can either the name or number where the options are:

* Low = 0
* Med = 5
* High = 10

        logwatch_detail: "Med"

The default time range for the Logwatch report.

    logwatch_range: "yesterday"

The output method of the Logwatch report.

    logwatch_output: "stdout"

The format of the Logwatch report.

    logwatch_format: "text"

The cron special time specification nickname - must match with logwatch range!

    logwatch_cron_time: "daily"

For Debian-based systems that use the Apt package manager, a check for packages that need to be updated can be performed and included in the daily report which is on by default.

    logwatch_updates_check: yes


Dependencies
------------

None.


Example Playbook
----------------

Simple version:

    - hosts: all
      roles:
        - paulrentschler.logwatch

Additional customizations:

    - hosts: all
      roles:
        - { role: paulrentschler.logwatch,
            logwatch_mail_to: "root@localhost, admin@example.net",
            logwatch_detail: "High",
            }


License
-------

[MIT][mit-link]


Author Information
------------------

Created by Paul Rentschler in 2021.


[mit-badge]: https://img.shields.io/badge/license-MIT-blue.svg
[mit-link]: https://github.com/paulrentschler/ansible-role-logwatch/blob/master/LICENSE
