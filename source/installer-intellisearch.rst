IntelliSearch Installer
=======================

The Qualtrak Coach IntelliSearch Installer.

Description
-----------

The Qualtrak Coach IntelliSearch Installer installs:

- IntelliSearch Producer Windows service.
- IntelliSearch Consumer Windows service.

IntelliSearch Producer
......................

Creates and queues IntelliSearch jobs for all Coach Tenants Searches.
IntelliSearch Producer is quick and low on consuming machine resources.

IntelliSearch Consumer
......................

Executes queued jobs from IntelliSearch Producer and gets from DataConnector endpoint media for particular Search Criteria, gets randomized media for User and saves all media for that IntelliSearch job.
Depending on numbers of Users for a particular IntelliSearch it can be time and machine resource consuming.

Usage
-----

.. note::
  Use ``config.intellisearch.ps1`` to set up *Coach IntelliSearch Installer* to meet desired needs.


- Get Help for *Qualtrak Coach IntelliSearch Installer* Cmdlet ``Install-CoachIntelliSearch``

  .. code-block:: powershell

  		Get-Help Install-CoachIntelliSearch -Full
  		Install-CoachIntelliSearch -?

* Run ``Install-CoachIntelliSearch`` to install *Coach IntelliSearch*. See *"Examples"* for more info or usage.

Examples
--------

.. note::
    - See more info about ``Coach-Install-Full`` parameters in *"Parameters"* section.
    - Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

- Minimal command usage. It will install both IntelliSearch Windows services (Producer and Consumer):

  .. code-block:: powershell

  	Install-CoachIntelliSearch

- Full command usage:

  .. code-block:: powershell

    Install-CoachIntelliSearch -Install Consumer -HA -StartingPort 9000


Parameters
----------

.. note::
  Please use single quotes ('') around parameter values, double quotes ("") values evaluate as *Powershell* statement, so it can have undesired effect!

-------

Install
.......

- Installs one or both IntelliSearch Windows service(s).
- Valid options: ``All``, ``Producer``, ``Consumer``.
- Default value is ``All`` or installing both IntelliSearch Windows services. So it can be used just as ``Install-CoachIntelliSearch`` without any parameter.


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
- Default value can be changed in ``config.intellisearch.ps1`` for property ``$global:startingPort`` it is by default set to ``9000``.

.. note::

  - If ``StartingPort`` parameter **will always override** ``config.intellisearch.ps1`` property ``$global:startingPort``!
  - If you want to use general default value use ``config.intellisearch.ps1`` property ``$global:startingPort``, if it is changeable use this ``StartingPort`` Parameter.
