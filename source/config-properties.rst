Config file properties
======================

The *Coach Installer* now has a ``config.ps1`` file that can be customized to meet the needs of *Qualtrak* partners for easier and
efficient *Coach* install process.

The properties in the ``config.ps1`` file should only be used where needed. Where they are not used, they will be ignored during the install.

*Microsoft Powershell* coding notation is used for editing the ``config.ps1`` script file.

-------

General
-------

General *Coach Installer* properties.

-------

Install Path
............

The install path for *Coach Installer*. Some development work outstanding so please do not change *Default Value*!

**Property Name**

    .. code-block:: powershell

    		$installPath

**Value**

	Single quoted string with standard *Windows* path notation e.g. ``c:\``.

**Default Value**

	Depending on system type:

	- ``'C:\Program Files'`` [x86]
	- ``'C:\Program Files (x86)'`` [x64]

-------

SSL
...

Whether *SSL* should be enabled or not.

**Property Name**

    .. code-block:: powershell

    		$isSSL

**Value**

	Boolean value: ``$true`` or ``$false``.

**Default Value**

	``$true``

-------

Coach System Administrator Username
...................................

Sets the *Coach* System Administrator username.
This is only required for a first-time installation. Where Coach is being upgraded the *System Admininstrator Username* value will be ignored.

**Property Name**

    .. code-block:: powershell

    		$sysAdminUsername

**Value**

	Single quoted string.

**Default Value**

	``'sys.admin'``

-------

Scheduler Trigger Time
......................

The time of day that the *Coach Scheduler Service* will run. Accepts 24 hour clock time.

**Property Name**

    .. code-block:: powershell

    		$schedulerTriggerTime

**Value**

	Single quoted string that represents time form ``'00:00'`` to ``'23:59'``.
	Please make sure to use leading zero time format e.g. ``01:30``!

**Default Value**

	``'02:00'``

-------

Install Instrumentation
.......................

Whether *Coach Instrumentation* will be installed.
Don't use *Coach Instrumentation* property in ``config.ps1``, if it is not needed!

**Property Name**

    .. code-block:: powershell

    		$installInstrumentation

**Value**

	Boolean value: ``$true`` or ``$false``.

**Default Value**

	Instead of default value don't use this property in ``config.ps1``!

-------


IIS
---

Internet Information Services (IIS) specific properties.

-------

Application Pool Name
.....................

The name of IIS Application Pool that *Coach* will be added to.

**Property Name**

    .. code-block:: powershell

    		$appPoolName

**Value**

	Single quoted string.

**Default Value**

	``'ASP.NET 4.0'``

-------

IIS Web Site Name
.................

The IIS Web Site Name that *Coach* Web Application will be part of.

**Property Name**

    .. code-block:: powershell

    		$iisWebSiteName

**Value**

	Single quoted string.

**Default Value**

	``'Default Web Site'``

-------

Web Application Name
....................

The *Coach* Web Application Name, that will be then used for main *Coach* URL, e.g. if name is set to "test", URL will be: ``https://example.com/test``.
This can be left as *Default Value* ``Coach`` but can be modified to fit with branding requirements.

**Property Name**

    .. code-block:: powershell

    		$appName

**Value**

	Single quoted string.

**Default Value**

	``Coach``

-------


Database
--------

The *Coach* SQL Server Database properties.

-------

Database Instance Name
......................

The SQL Server Database Instance or Server name for where *Coach* database will be installed.
Use this property if the Instance name is not changing, but if the Instance name does need to be changed then use *Qualtrak Coach Installer* parameter ``-DbSrv`` with instance/server name.

**Property Name:**

    .. code-block:: powershell

    		$dbInstanceName

**Value**

	Single quoted string. Any valid SQL Server named instance or server name.

**Default Value**

	``.\SQLEXPRESS``

-------

Database Login Name (User)
..........................

The SQL Server Database Login name (Db User) needed for *Coach* database and scripts to run and install properly. The Login name must have ``sysadmin`` role in SQL Server *Server Roles*.
Use this property if the same login name is used for all deployments, otherwise use *Qualtrak Coach Installer* parameter ``-DbUsr`` with login name.
This value is only persisted here in ``config.ps1`` as it is only needed for installation session.
If persisting to ``config.ps1`` is a problem then use *Qualtrak Coach Installer* parameter ``-DbUsr`` instead.

**Property Name**

    .. code-block:: powershell

    		$dbLoginName

**Value**

	Single quoted string.

**Default Value**

	``sa``

-------


web.config
----------

The ASP.NET ``web.config`` properties currently for ``<appSettings>``, ``<machineKey>`` and ``<authentication>``.

-------

Authentication Route
....................

Used to mark that *Coach* integration Authentication Route will be through a URL query string.
It will add to the *Coach* ``web.config`` in ``<appSettings>`` element new setting with key ``AuthenticationRoute`` with value ``url``.
Don't use *Authentication Route* property in ``config.ps1``, if it is not needed!

**Property Name**

    .. code-block:: powershell

    		$authenticationRoute

**Value**

	Single quoted string.

**Default Value**

	Instead of default value don't use this property in ``config.ps1``!

-------

Machine Validation Key
......................

Sets the custom Machine Validation ``SHA1`` Key to *Coach* ``web.config`` ``<machineKey>`` element.
Don't use *Machine Validation Key* property in ``config.ps1``, if it is not needed!

**Property Name**

    .. code-block:: powershell

    		$machineValidationKey

**Value**

	Single quoted ``SHA1`` string.

**Default Value**

	Instead of default value don't use this property in ``config.ps1``!

-------

Machine Decription Key
......................

Sets the custom Machine Decryption ``AES`` Key to *Coach* ``web.config`` ``<machineKey>`` element.
Don't use *Machine Validation Key* property in ``config.ps1``, if it is not needed!

**Property Name**

    .. code-block:: powershell

    		$machineDecryptionKey

**Value**

	Single quoted ``AES`` string.

**Default Value**

	Instead of default value don't use this property in ``config.ps1``!

-------

Authentication Forms Name
.........................

Sets the custom Forms Name attribute to *Coach* ``web.config`` ``<forms>`` element.
Don't use *Authentication Forms Name* property in ``config.ps1``, if it is not needed!

**Property Name**

    .. code-block:: powershell

    		$formsName

**Value**

	Single quoted string.

**Default Value**

	Instead of default value don't use this property in ``config.ps1``!

-------

Authentication Forms Domain
...........................

Sets the custom Forms Domain attribute to *Coach* ``web.config`` ``<forms>`` element.
Don't use *Authentication Forms Domain* property in ``config.ps1``, if it is not needed!

**Property Name**

    .. code-block:: powershell

    		$formsDomain

**Value**

	Single quoted string.

**Default Value**

	Instead of default value don't use this property in ``config.ps1``!

-------


Windows Authentication
----------------------

Enables Windows Authentication in *Coach*.
If Windows Authentication is not needed don't include any of its properties in ``config.ps1``.

-------

Windows Authentication
......................

Enables Windows Authentication in *Coach*. This also requires the *Active Directory Group Name* property to be set.
Don't use *Windows Authentication* property in ``config.ps1``, if it is not needed!

**Property Name**

    .. code-block:: powershell

    		$isWindowsAuth

**Value**

	Boolean value: ``$true`` or ``$false``.

**Default Value**

	Instead of default value don't use this property in ``config.ps1``!

-------

Active Directory Group Name
...........................

Sets the custom *Active Directory* group name.
Don't use *Active Directory Group Name* property in ``config.ps1``, if it is not needed!

**Property Name**

    .. code-block:: powershell

    		$activeDirectoryGroupName

**Value**

	Single quoted string.

**Default Value**

	Instead of default value don't use this property in ``config.ps1``!

-------


Recorder
--------

Recorder specific properties for IP address and database connection details.

-------

Recorder IP Address
...................

The IP address of the Recorder that *Coach* will integrate with.
Use this property if the same Recorder IP address is used for all deployments. If not, then use *Qualtrak Coach Installer* parameter ``-RecorderIP`` with valid IP address.

**Property Name**

    .. code-block:: powershell

    		$recorderIpAddress

**Value**

	Single quoted string as valid IP address.

**Default Value**

	``localhost``

-------

Recorder Database Instance Name
...............................

The Database instance name that the Recorder uses for persisting recordings.

**Property Name**

    .. code-block:: powershell

    		$dbRecorderInstance

**Value**

	Single quoted string.

**Default Value**

	``'.\SQLEXPRESS'``

-------

Recorder Database Login Name
............................

The Database login (user) name that the Recorder uses for persisting recordings.

**Property Name**

    .. code-block:: powershell

    		$dbRecorderLoginName

**Value**

	Single quoted string.

-------

Recorder Database Login Password
................................

The Database login (user) password that the Recorder uses for persisting recordings.

**Property Name**

    .. code-block:: powershell

    		$dbRecorderPasswd

**Value**

	Single quoted string.

-------

HA (High Availability)
----------------------

HA specific properties currently for ASP.NET Identity/Shared Folder, ASP.NET Session State and Database.

.. note::
  HA properties are included in all config files, except ``config.db.ps1``, but commented out by default.


.. note::
  To setup HA:
  * **ASP.NET Identity and Shared Folder**: it is required to set values for File share Username, Password and Path. If not. it will not be applied!
  * **ASP.NET Session State: State Server**: it is required to set values for Session State mode (as `StateServer`), IP address and port. If not, it will not be applied!
  * **ASP.NET Session State: SQL Server**: it is required to set values for Session State mode (as 'SQLServer'), SQL Server IP address and SQL Server Failover Partner IP address.
  * **Datbase**: it is required to set values for SQL Server IP address and SQL Server Failover Partner IP address.

-------

ASP.NET Identity and Shared Folder
..................................


File share Username
+++++++++++++++++++

The File share username used for Coach attachments folder on server as ASP.NET Identity.

**Property Name**

    .. code-block:: powershell

    		$fileShareUsername

**Value**

	Single quoted string.

-------

File share Password
+++++++++++++++++++

The File share password used for Coach attachments folder on server as ASP.NET Identity.

**Property Name**

    .. code-block:: powershell

    		$fileSharePassword

**Value**

	Single quoted string.

-------

File share Path
+++++++++++++++

The File share path used for Coach attachments folder on server.

**Property Name**

    .. code-block:: powershell

    		$fileSharePath

**Value**

	Single quoted string.

-------

ASP.NET Session State
.....................

Session State Mode
++++++++++++++++++

The ASP.NET session state mode, supported is both ``StateServer`` and ``SqlServer`` ASP.NET Session State mode.

**Property Name**

    .. code-block:: powershell

    		$sessionStateMode

**Value**

	Single quoted string.

**Default Value**

	``'SQLServer'``

-------

ASP.NET Session State: State Server
...................................

Session State IP address
++++++++++++++++++++++++

The ASP.NET Session State Server IP address.

**Property Name**

    .. code-block:: powershell

    		$sessionStateIP

**Value**

	Single quoted string. Valid IP address or DNS name.

-------

Session State Port
++++++++++++++++++

The ASP.NET Session State IP address Port.

**Property Name**

    .. code-block:: powershell

		    $sessionStatePort

**Value**

	Integer value. Greater than zero (0).

**Default Value**

	``42424``

Database & ASP.NET Session State: SQL Server
................................................

SQL Server IP address
+++++++++++++++++++++

The SQL Server IP address.

**Property Name**

    .. code-block:: powershell

    		$sqlServerIP

**Value**

	Single quoted string. Valid IP address or DNS name.

-------

SQL Server Failover Partner IP address
++++++++++++++++++++++++++++++++++++++

The SQL Server Failover Partner IP address.

**Property Name**

    .. code-block:: powershell

    		$sqlServerFailoverPartnerIP

**Value**

	Single quoted string. Valid IP address or DNS name.

-------

TLM (Tenant and Licensing management & real-time Monitoring)
------------------------------------------------------------

TLM (Coach Tenant and License Management) properties that will set up the URI of TLM.

.. note::
  Available in ``config.ps1`` and in ``config.tlm.ps1``.

-------

TLM IP address
..............

TLM (Tenant and Licensing management & real-time Monitoring) IP address.
Port for IP address is set from property ``StartingPort`` and it is usually one number higher
``StartingPort``, e.g. if ``StartingPort`` is ``9000`` the TLM IP address port will be ``9001``.

**Property Name**

    .. code-block:: powershell

		    $tlmIp

**Value**

	Single quoted string. Valid IP address or DNS name.

**Default Value**

	``'127.0.0.1'``

-------

Akka Coach Seed
---------------

Akka Coach seed specific properties. Where seed node list is used in all *Coach Akka Win Services*.
Available in all configs except ``config.db.ps1``, for seed nodes list and starting port,
and Public IP address available only in *HA* installation.

-------

Seed Public IP address
......................

Coach Akka Seed IP address. Only applicable for *HA* installations.
Port is used from property ``StartingPort`` but it is only used when it is a *HA* installation.
For *non-HA* installation port ``0`` is used.

**Property Name**

    .. code-block:: powershell

    		$seedPublicHostname

**Value**

	Single quoted string. Valid IP address or DNS name.

-------

Starting Port
.............

Port for *Coach Akka Seed* IP address and TLM IP address.
In *non-HA* installation used only for TLM IP address port, in *HA* installation can be
used with installer switch ``-StartingPort`` to apply sliding ports on multiple VM's
since port must be unique on multiple VM's for same *Seed Public IP address*.

**Property Name**

    .. code-block:: powershell

		    $global:startingPort

**Value**

	Integer value. Greater than zero (0).

**Default Value**

	``9000``


Seed Nodes list
...............

List of multiple *Coach Akka* seed nodes.

**Property Name**

    .. code-block:: powershell

		    $seedNodes

**Value**

	Powrshell array ``@()`` of single quoted string and comma separated. [IP|DNS]:Port format.

**Default Value**

	``@('127.0.0.1:9001')``
