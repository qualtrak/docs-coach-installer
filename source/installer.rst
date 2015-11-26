Full Installer
==============

The Qualtrak Coach Full Installer.

Description
-----------

The Qualtrak Coach Installer installs:

- Coach Web Application.
- Data Connector integration.
- IntelliSearch Windows Services (Producer and Consumer).
- TLM (Tenant and Licensing management & real-time Monitoring) Web App and Windows Service.
- Akka Coach Seed Windows Service
- Coach REST API (*C# Wrapper*)[Optional].

.. warning::
  Please make sure to backup all your data before running *Qualtrak Coach Installer* to make sure of no data loss!


Usage
-----

.. note::
  Use ``config.ps1`` to set up *Coach Full Installer* to meet desired needs.

- Get Help for *Qualtrak Coach Installer* Cmdlet ``Install-CoachFull``

  .. code-block:: powershell

  		Get-Help Install-CoachFull -Full
  		Install-CoachFull -?

- Run ``Install-CoachFull`` to install *Coach*. See *"Examples"* for more info or usage.

Examples
--------

.. note::
    - See more info about ``Install-CoachFull`` parameters in *"Parameters"* section.
    - Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

- Minimal command with usage of required parameter ``DbPasswd``. If omitted, user will be prompted to enter manually:

  .. code-block:: powershell

  		Install-CoachFull -DbPasswd '$ecReT'

Full example with all parameters. Note that ``-SysPasswd`` is only needed for first-install of Coach.:

  .. code-block:: powershell

  		Install-CoachFull -DbSrv 'srv\ins' -DbUsr 'admin' -DbPasswd '$ecReT' -RecorderIP '10.0.0.1' -SysPasswd 'P@$$w0rd' -HA -StartingPort 9000


Parameters
----------

.. note::
    - Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!
    - If ``AspireUser`` *(Coach database User)* is used as ``DbUsr`` parameter or ``$global:dbLoginName`` property is set in ``config.ps1`` then in Coach database connection string ``DbPasswd`` parameter value will be used, overriding default Coach database connection string password value.


-------

DbSrv
.....

- Specifies the *SQL Server* database server\instance.
- General default value can be changed in ``config.ps1`` for property ``$dbInstanceName`` it is by default set to ``.\SQLEXPRESS``.

.. note::

    - ``DbSrv`` parameter **will always override** ``config.ps1`` property ``$global:dbInstanceName``!
    - If you want to use general default value use ``config.ps1`` property ``$global:dbInstanceName``, if it is changeable use this ``DbSrv`` Parameter.

-------

DbUsr
.....

- Specifies the *SQL Server* database server\instance user login name.
- This value is not **persisted or saved** in any way, it is **only** for lifetime of installation session. Unless user used is ``AspireUser`` which is Coach database user used in connection string.
- General default value can be changed in ``config.ps1`` for property ``$global:dbLoginName`` it is by default set to ``$null``.

.. note::

    - ``DbUsr`` parameter **will always override** ``config.ps1`` property ``$global:dbLoginName``!
    - If you want to use general default value use ``config.ps1`` property ``$global:dbLoginName``, if it is changeable use this ``DbUsr`` Parameter.

-------

DbPasswd
........

- Specifies the *SQL Server* database server\instance password.
- This value is not **persisted or saved** in any way, it is **only** for lifetime of installation session. Unless ``DbUsr`` parameter value is ``AspireUser`` which is default Coach database user used in connection string. Then ``DbPasswd`` value will override default password for Cocah database connection string.
- **Required**.

.. note::

    - If not specified will stop script and wait for ``DbPasswd`` enter manually in prompt!
    - If ``DbPasswd`` value is whitespace it will terminate the script!

-------

RecorderIP
..........

- Specifies the Recorder IP address with any valid IP Address or DNS name.
- General default value can be changed in ``config.ps1`` for property ``$global:recorderIpAddress`` it is by default set to ``localhost``.

.. note::

    - If ``RecorderIP`` parameter **will always override** ``config.ps1`` property ``global:$recorderIpAddress``!
    - If you want to use general default value use ``config.ps1`` property ``$global:recorderIpAddress``, if it is changeable use this ``RecorderIP`` Parameter.

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

HA
..

- Tells to installer that this is *HA* installation and sometimes in combination with ``StartingPort`` when there is need for sliding number for ports in *HA*.
- If used then will set installer to be in a *HA mode*, if not it will do normal *Single Server* install.

-------

StartingPort
............

- Only usable with ``HA`` switch and in *HA mode*.
- Specifies the starting port and it can be used to set sliding ports when multiple installers used in multiple VM's.
- Sliding port means each *HA* VM's with Coach components needs unique port number(s).
- Default value can be changed in ``config.ps1`` for property ``$global:startingPort`` it is by default set to ``9000``.

.. note::

  - If ``StartingPort`` parameter **will always override** ``config.ps1`` property ``$global:startingPort``!
  - If you want to use general default value use ``config.ps1`` property ``$global:startingPort``, if it is changeable use this ``StartingPort`` Parameter.
