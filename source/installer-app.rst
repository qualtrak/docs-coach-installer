App Installer
=============


The Qualtrak Coach App Installer.

Description
-----------

The Qualtrak Coach App Installer installs:

- Coach Web Application.
- DataConnector integration Web API/Service.
- IntelliSearch [Optional].
- Coach REST API (*C# Wrapper*)[Optional].

Usage
-----

.. note::
  Use ``config.app.ps1`` to set up *Coach App Installer* to meet desired needs.


- Get Help for *Qualtrak Coach App Installer* Cmdlet ``Install-CoachApp``

  .. code-block:: powershell

  		Get-Help Install-CoachApp -Full
  		Install-CoachApp -?

- Run ``Install-CoachApp`` to install *Coach*. See *"Examples"* for more info or usage.

Examples
--------

.. note::
    - See more info about ``Install-CoachApp`` parameters in *"Parameters"* section.
    - Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

- Minimal command usage:

  .. code-block:: powershell

  	Install-CoachApp

- Full command usage:

  .. code-block:: powershell

  	Install-CoachApp -IntelliSearch All -HA -StartingPort 9000

Parameters
----------

.. note::
  Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

-------

IncludingTLMWeb
...............

- If it is used during installation it will include TLM Web in installation, otherwise it will not.

-------

IntelliSearch
.............

- It can include IntelliSearch Windows Service(s). ``All`` it will install Producer and Consumer Windows Services, or ``Producer`` or ``Consumer`` by itself.
- Valid options: ``All``, ``Producer``, ``Consumer``.
- Default value is ``All`` or not installing IntelliSearch.


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
