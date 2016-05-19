Update Coach Install
====================


Checklist
---------

- Check validity of values in *<installer folder>\\config.ps1*. If in doubt check :ref:`Config file properties <config-properties>`.
- If your SQL Server instance is different than ``.\SQLEXPRESS`` make sure to enter proper one for property ``$global:dbInstanceName`` in ``config.ps1``.

.. note::

 Currently if ``sa`` or SQL server system user is not avaialble. It is possible to use Coach SQL server user ``AspireUser`` created on fresh install, it has a default password set to ``password``. 
 If this is a security issue ask DB admin to create new password for user ``AspireUser`` and use it in install.

 Currently installer only support Database users with SQL Authorization. SQL Server Windows Authentication is not supported.

.. important::

 For Coach IntegrationSDK install partners, please before running install make sure to overwrite ``02_partner_integrationsdk.sql`` with your own Coach integration T-SQL file in *<installer folder>\\db*. Make sure that you use script file with Recorder IP adress set for this deployment.
 

Pre-Install
-----------

- Download installer.
- Unblock installer zip file (by right click > Properties > Unblock) .
- Extract installer zip.
- Open *Powershell* console as *Administrator*.
- ``cd`` into extracted installer folder.
- Run installer setup by:

.. code-block:: shell

        .\InstallerSetup.ps1


Installation
------------
        
- Run Full *Qualtrak Coach Installer*
- ``DbPaswd`` is required. If not entered installer will prompt for entering SQL server user password.

.. code-block:: shell

        Install-CoachFull -DbPasswd '<db user password>' 
        


Post Install
------------

After successful installation sign in into *Coach* first time, use this values in login page:

- **Tenant Code**: ``1000``
- **Username**: ``sys.admin``
- **Password**: password entered for Coach System Administrator on first install (installer switch ``SysPasswd``, if used or when prompted).