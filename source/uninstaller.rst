Uninstaller
===========

Partial Uninstall
.................

The Qualtrak Coach partial uninstall.

Description
-----------

On each update for new release partial uninstall is used to remove only *Coach* files and binaries, needed to be cleaned up for newer release files and binaries.

Each installer [``Full``, ``App``, ``Db``, ``IntelliSearch``, ``TLM``] can be uninstalled with partial uninstaller.


Usage
-----

- Get Help for *Qualtrak Coach Installer* Cmdlet ``Coach-Uninstall``

	.. code-block:: powershell

			Get-Help Coach-Uninstall -Full
			Coach-Uninstall -?

- Run ``Uninstall-Coach`` to update and partially uninstall *Coach*. See *"Examples"* for more info or usage.

Examples
--------

.. note::
  - See more info about ``Coach-Uninstall`` parameters in *"Parameters"* section.
  - Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

- Minimal usage, it will uninstall Qualtrak Coach Full installer files:

	.. code-block:: powershell

			Coach-Uninstall
			# same as it was used:
			Uninstall-Coach -Installer Full


- Full usage for uninstall particular Qualtrak Coach installer with all supported installers:

	.. code-block:: powershell

		Uninstall-Coach -Installer Full
		Uninstall-Coach -Installer App
		Uninstall-Coach -Installer IntelliSearch
		Uninstall-Coach -Installer TLM


Parameters
----------

.. note::
  - Please use single quotes ('') around parameter values, double quotes ("") values evalute as *Powershell* statement, so it can have undesired effect!

-------

Installer
.........

- Set of Qualtrak Coach supported installers that can be uninstalled for speceific installer.
- All except *Coach* ``Db`` installer have their equivalent uninstaller. 
- Valid options: ``Full``, ``App``, ``IntelliSearch``, ``TLM``.
- Default value is ``Full``. So it can be used just as ``Uninstall-Coach`` without any parameter.

-------

Full Uninstall
.................

The Qualtrak Coach full uninstall.

Description
-----------

The uninstaller removes *Coach* completely from the system.

.. warning::
	Beware with this command all data will be lost files, binaries, uploaded files and Coach database.

.. note::

	Full installer removes:
	- *Coach* Windows Services.
	- *Coach IIS Web* applications.
	- Drops *Coach* database, and database User Login used for *Coach* (``AspireUser``).
	- All *Coach* files from disk.

Usage
-----

- Get Help for *Qualtrak Coach Installer* Cmdlet ``Uninstall-CoachAll``

	.. code-block:: powershell

		Get-Help Uninstall-CoachAll -Full
		Uninstall-CoachAll -?

- Run ``Uninstall-CoachAll`` to fully uninstall *Coach*. See *"Examples"* for more info or usage.

Examples
--------

.. note:
  - See more info about ``Coach-UninstallAll`` parameters in *"Parameters"* section.
  - Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

- Minimal usage, used for complete remove of Coach from system, with minimal (required) parameters:

	.. code-block:: powershell

			Uninstall-CoachAll -DbPasswd '$ecReT'


- Full usage of uninstaller parameters, used for complete remove of *Coach* from system with all parameters:

	.. code-block:: powershell

		Uninstall-CoachAll -DbSrv 'srv\ins' -DbUsr 'admin' -DbPasswd '$ecReT'

-------


Parameters
----------

.. note::
  - Please use single quotes ('') around parameter values, double quotes ("") values evalute as *Powershell* statement, so it can have undesired effect!

DbSrv
.....

* Specifies the *SQL Server* database server\instance.
* General default value can be changed in ``config.ps1`` for property ``$global:dbInstanceName`` it is by default set to ``.\SQLEXPRESS``.

.. note::

    - ``DbSrv`` parameter **will always override** ``config.ps1`` property ``global:$dbInstanceName``!
    - If you want to use general default value use ``config.ps1`` property ``global:$dbInstanceName``, if it is changeable use this ``DbSrv`` Parameter.

-------

DbUsr
.....

- Specifies the *SQL Server* database server\instance user login name.
- This value is not **persisted or saved** in any way, it is **only** for lifetime of installation session.
- General default value can be changed in ``config.ps1`` for property ``$global:dbLoginName`` it is by default set to ``$null``.

.. note::

    - ``DbUsr`` parameter **will always override** ``config.ps1`` property ``$global:dbLoginName``!
    - If you want to use general default value use ``config.ps1`` property ``$global:dbLoginName``, if it is changeable use this ``DbUsr`` Parameter.

-------

DbPasswd
........

- Specifies the *SQL Server* database server\instance password.
- This value is not **persisted or saved** in any way, it is **only** for lifetime of installation session.
- **Required** when parameter ``Full`` is used.

.. note::

    - If not specified it will stop script and wait for ``DbPasswd`` enter manually in prompt!
    - If ``DbPasswd`` value is whitespace it will terminate the script!
