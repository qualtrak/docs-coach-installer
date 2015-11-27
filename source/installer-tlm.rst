TLM Installer
=============


The Qualtrak Coach TLM Installer.

Description
-----------

The Qualtrak Coach TLM (Tenant and Licensing management & real-time Monitoring) Installer installs:

- TLM Windows Service.
- TLM Web Application.
- Akka Coach Seed Windows Service [Optional].
- Coach REST API (*C# Wrapper*)[Optional].

Usage
-----

.. note::
  Use ``config.tlm.ps1`` to set up *Coach TLM Installer* to meet desired needs.


- Get Help for *Qualtrak Coach TLM Installer* Cmdlet ``Install-CoachTLM``

  .. code-block:: powershell

  		Get-Help Install-CoachTLM -Full
  		Install-CoachTLM -?

- Run ``Install-CoachTLM`` to install *Coach*. See *"Examples"* for more info or usage.

Examples
--------

.. note::
    - See more info about ``Install-CoachTLM`` parameters in *"Parameters"* section.
    - Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

- Minimal command usage:

  .. code-block:: powershell

  	Install-CoachTLM

- Full command usage:

  .. code-block:: powershell

  	Install-CoachTLM -IncludingSeed -HA -StartingPort 9000

Parameters
----------

.. note::
  Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

-------

IncludingSeed
.............

- If it is used during installation it will include *Akka Coach Seed* Windows Service in installation, otherwise it will not.

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
- Default value can be changed in ``config.app.ps1`` for property ``$global:startingPort`` it is by default set to ``9000``.

.. note::

  - If ``StartingPort`` parameter **will always override** ``config.app.ps1`` property ``$global:startingPort``!
  - If you want to use general default value use ``config.app.ps1`` property ``$global:startingPort``, if it is changeable use this ``StartingPort`` Parameter.
