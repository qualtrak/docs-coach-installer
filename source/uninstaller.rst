Uninstaller
===========

The Qualtrak Coach Uninstaller.

Description
-----------

The update to new release and full *Coach Uninstaller*:

- *Update to new release* uninstaller removes only *Coach* files and binaries, needed to be cleaned up for newer release.
- *Full* uninstaller removes *Coach* completely from the system.


Usage
-----

- Get Help for *Qualtrak Coach Installer* Cmdlet ``Uninstall-Coach``

.. code-block:: powershell

		Get-Help Uninstall-Coach -Full
		Uninstall-Coach -?

- Run ``Uninstall-Coach`` to uninstall *Coach*. See "*Examples*" for more info or usage.

Examples
--------

.. note:
    - See more info about ``Uninstall-Coach`` parameters in "*Parameters*" section.
    - Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

- Minimal usage, used for update to new release version, removes files and Coach binaries, safe to use:

.. code-block:: powershell

		Uninstall-Coach

- Minimal usage for full uninstall, used for complete remove of Coach from system, **beware of losing data**, unsafe to use.

.. code-block:: powershell

		Uninstall-Coach -Full -DbPasswd '$ecRT'

- Full usage of uninstaller parameters, used for complete remove of Coach from system, **beware of losing data**, unsafe to use:

.. code-block:: powershell

		Uninstall-Coach -Full -DbSrv 'srv\ins' -DbUsr 'admin' -DbPasswd '$ecRT'


Parameters
----------

.. note::
  - Please use single quotes ('') around parameter values, double quotes ("") values evalute as *Powershell* statement, so it can have undesired effect!

-------

Full
....

- The full unistall of Coach.

.. warning::
    - **Beware,using this parameter will erase all your Coach data**

.. note::

    - Removes *Coach Scheduler* Win Service.
    - Removes *IIS Web* applications.
    - Drops the *Coach* Database.
    - Remove all *Coach* files from disk.

-------

DbSrv
.....

* Specifies the *SQL Server* database server\instance.
* General default value can be changed in ``config.ps1`` for property ``$dbInstanceName`` it is by default set to ``.\SQLEXPRESS``.

.. note::

    - Applicable only when ``Full`` parameter is used.
    - ``DbSrv`` parameter **will always override** ``config.ps1`` property ``$dbInstanceName``!
    - If you want to use general default value use ``config.ps1`` property ``$dbInstanceName``, if it is changeable use this ``DbSrv`` Parameter.

-------

DbUsr
.....

- Specifies the *SQL Server* database server\instance user login name.
- This value is not **persisted or saved** in any way, it is **only** for lifetime of installation session.
- General default value can be changed in ``config.ps1`` for property ``$dbLoginName`` it is by default set to ``$null``.

.. note::

    - Applicable only when ``Full`` parameter is used.
    - ``DbUsr`` parameter **will always override** ``config.ps1`` property ``$dbLoginName``!
    - If you want to use general default value use ``config.ps1`` property ``$dbLoginName``, if it is changeable use this ``DbUsr`` Parameter.

-------

DbPasswd
........

- Specifies the *SQL Server* database server\instance password.
- This value is not **persisted or saved** in any way, it is **only** for lifetime of installation session.
- **Required** when parameter ``Full`` is used.

.. note::

    - Applicable only when ``Full`` parameter is used.
    - If not specified when ``Full`` parameter is used, it will stop script and wait for ``DbPasswd`` enter manually in prompt!
    - If ``DbPasswd`` value is whitespace it will terminate the script!

-------
