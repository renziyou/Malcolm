# Hedgehog Linux

**Network Traffic Capture Appliance**

![Hedgehog Linux](./images/hedgehog/logo/hedgehog-color-w-text.png)

Hedgehog Linux is a Debian-based operating system built to

* monitor network interfaces
* capture packets to PCAP files
* detect file transfers in network traffic and extract and scan those files for threats
* generate and forward Zeek logs, Arkime sessions and other information to [Malcolm]({{ site.github.repository_url }})

![sensor-iso-build-docker-wrap-push-ghcr]({{ site.github.repository_url }}/workflows/sensor-iso-build-docker-wrap-push-ghcr/badge.svg)

<a name="HedgehogTableOfContents"></a>
* [Sensor installation](hedgehog-installation.md#HedgehogInstallation)
    - [Image boot options](hedgehog-installation.md#HedgehogBootOptions)
    - [Installer](hedgehog-installation.md#HedgehogInstaller)
* [Boot](hedgehog-boot.md#HedgehogBoot)
    - [Kiosk mode](hedgehog-boot.md#HedgehogKioskMode)
* [Configuration](hedgehog-config.md#HedgehogConfiguration)
    - [Interfaces, hostname, and time synchronization](hedgehog-config-root.md#HedgehogConfigRoot)
        + [Hostname](hedgehog-config-root.md#HedgehogConfigHostname)
        + [Interfaces](hedgehog-config-root.md#HedgehogConfigIface)
        + [Time synchronization](hedgehog-config-root.md#HedgehogConfigTime)
    - [Capture, forwarding, and autostart services](hedgehog-config-user.md#HedgehogConfigUser)
        + [Capture](hedgehog-config-user.md#HedgehogConfigCapture)
            * [Automatic file extraction and scanning](hedgehog-config-user.md#HedgehogZeekFileExtraction)
        + [Forwarding](hedgehog-config-user.md#HedgehogConfigForwarding)
            * [arkime-capture](hedgehog-config-user.md#Hedgehogarkime-capture): Arkime session forwarding
            * [filebeat](hedgehog-config-user.md#Hedgehogfilebeat): Zeek and Suricata log forwarding
            * [miscbeat](hedgehog-config-user.md#Hedgehogmiscbeat): System metrics forwarding        
        + [Autostart services](hedgehog-config-user.md#HedgehogConfigAutostart)
+ [Zeek Intelligence Framework](hedgehog-config-zeek-intel.md#HedgehogZeekIntel)
* [Appendix A - Generating the ISO](hedgehog-iso-build.md#HedgehogISOBuild)
* [Appendix B - Configuring SSH access](hedgehog-ssh.md#HedgehogConfigSSH)
* [Appendix C - Troubleshooting](hedgehog-troubleshooting.md#HedgehogTroubleshooting)
* [Appendix D - Hardening](hedgehog-hardening.md#HedgehogHardening)
    - [Compliance exceptions](hedgehog-hardening.md#HedgehogComplianceExceptions)
* [Appendix E - Upgrades](hedgehog-upgrade.md#HedgehogUpgradePlan)
