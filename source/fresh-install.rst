Fresh Install
=============

.. note::

 Before installing *Qualtrak Coach Installer* please make sure that system requirements are met and `server is configured for Coach <http://data-connector-api.readthedocs.io/en/latest/server.html#server-deploy-label>`_.

Checklist
---------

- Check validity of values in *<installer folder>\\config.ps1*. If in doubt check :ref:`Config file properties <config-properties>`.
- If your SQL Server instance is different than ``.\SQLEXPRESS`` make sure to enter proper one for property ``$global:dbInstanceName`` in ``config.ps1``.
- Make sure that SQL Server user is ``sa`` or any user with SQL Server system role. Only needed for fresh install. 

.. note::

 Currently fresh install requires SQL Server system role for creating Database and SQL User for *Coach*. 
 If this is a problem ask DB admin to create new user with SQL system role, that can be removed after first install.

 Currently installer only support Database users with SQL Authorization. SQL Server Windows Authentication is not supported.

.. note::

 For Coach IntegrationSDK install partners, please before running install make sure to overwrite ``02_partner_integrationsdk.sql`` with your own integration SQL file in *<installer folder>\\db*.

Pre-Install
-----------

- Download installer.
- Unblock installer zip file (by right click > Properties > Unblock).
- Extract installer zip.
- Open *Powershell* console as *Administrator*.
- ``cd`` into extracted installer folder.
- Run installer setup by:

.. code-block:: shell

        .\InstallerSetup.ps1


Installation
------------
        
- Run Full *Qualtrak Coach Installer*
- ``DbPaswd`` and ``SysPasswd`` are required. If not entered installer will prompt for entering them.

.. code-block:: shell

        Install-CoachFull -DbPasswd <db user password> -SysPasswd <coach system administrator password>
        
.. note::

 Coach System Administrator is role used to create Tenants and shold be used only for that. 
 Do not add this Coach System Administrator to any Tenant organization hierarchy. 


Post Install
------------

After successful installation sign in into *Coach* first time, use this values in login page:

- **Tenant Code**: ``1000``
- **Username**: ``sys.admin``
- **Password**: password entered for Coach System Administrator on first install (installer switch ``SysPasswd``, if used or when prompted).

.. note::

 *Coach System Administrator* username is by default set to ``sys.admin``. If there is need for other username please use config property ``$sysAdminUsername`` in *<installer folder>\\config.ps1* to set desired username for *Coach System Administrator* user.