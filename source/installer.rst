Full Installer
=========

The Qualtrak Coach Full Installer.

Description
-----------

The Qualtrak Coach Installer installs:

- Coach Web Application.
- Recorder integration Web Service.
- Scheduler Windows Service.
- REST API (*Docs and Wrapper*)[Optional].

.. warning::
  Please make sure to backup all your data before running *Qualtrak Coach Installer* to make sure of no data loss!

Usage
-----

- Get Help for *Qualtrak Coach Installer* Cmdlet ``Coach-Install-Full``

.. code-block:: powershell

		Get-Help Coach-Install-Full -Full
		Coach-Install-Full -?

- Run ``Coach-Install-Full`` to install *Coach*. See "*Examples*" for more info or usage.

Examples
--------

.. note::
    - See more info about ``Coach-Install-Full`` parameters in "*Parameters*" section.
    - Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

- Minimal command with usage of required parameter ``DbPasswd``. If omitted, user will be prompted to enter manually:

.. code-block:: powershell

		Coach-Install-Full -DbPasswd 'secReT'

Full example with all parameters. Note that "-SysPasswd" is only needed for first-install of Coach.:

.. code-block:: powershell

		Coach-Install-Full -DbSrv 'srv\ins' -DbUsr 'admin' -DbPasswd '$ecReT' -RecorderIP '10.0.0.1' -SysPasswd 'P@$$w0rd'


Parameters
----------

.. note::
    Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

-------

DbSrv
.....

- Specifies the *SQL Server* database server\instance.
- General default value can be changed in ``config.ps1`` for property ``$dbInstanceName`` it is by default set to ``.\SQLEXPRESS``.

.. note::

    - ``DbSrv`` parameter **will always override** ``config.ps1`` property ``$dbInstanceName``!
    - If you want to use general default value use ``config.ps1`` property ``$dbInstanceName``, if it is changeable use this ``DbSrv`` Parameter.

-------

DbUsr
.....

- Specifies the *SQL Server* database server\instance user login name.
- This value is not **persisted or saved** in any way, it is **only** for lifetime of installation session.
- General default value can be changed in ``config.ps1`` for property ``$dbLoginName`` it is by default set to ``$null``.

.. note::

    - ``DbUsr`` parameter **will always override** ``config.ps1`` property ``$dbLoginName``!
    - If you want to use general default value use ``config.ps1`` property ``$dbLoginName``, if it is changeable use this ``DbUsr`` Parameter.

-------

DbPasswd
........

- Specifies the *SQL Server* database server\instance password.
- This value is not **persisted or saved** in any way, it is **only** for lifetime of installation session.
- **Required**.

.. note::

    - If not specified will stop script and wait for ``DbPasswd`` enter manually in prompt!
    - If ``DbPasswd`` value is whitespace it will terminate the script!

-------

RecorderIP
..........

- Specifies the Recorder IP address with any valid IP Address or DNS name.
- General default value can be changed in ``config.ps1`` for property ``$recorderIpAddress`` it is by default set to ``localhost``.

.. note::

    - If ``RecorderIP`` parameter **will always override** ``config.ps1`` property ``$recorderIpAddress``!
    - If you want to use general default value use ``config.ps1`` property ``$recorderIpAddress``, if it is changeable use this ``RecorderIP`` Parameter.

-------

SysPasswd
.........

- Specifies the Coach System Administrator password.
- It is **required** on *Coach* first-install.

.. note::

    - If not specified on *Coach* first-install it will stop script and wait for ``SysPasswd`` enter manually in prompt!
    - If ``SysPasswd`` value is empty or whitespace it will terminate the script!
    - If used on *Coach* release update will display warning, because in that case ``SysPasswd`` will be completely ignored by install.

-------
