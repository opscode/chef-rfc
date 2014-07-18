# Chef Platform Support Policy

The purpose of this RFC is to clarify:

* What specific operating system platforms and platform versions are supported by the software produced by Chef Software, Inc.
* What is the meaning of "supported platform"

This RFC does *not* address "What is the product lifecycle of Chef Software, Inc.'s software". That is covered in a separate RFC

## Chef Client

A Chef Client supported platform means:

* Omnitruck won't fail or go into Yolo mode when confronted with the platform
* The holy trinity of resources (package, service, template) works out of the box
* Ohai attributes for ```platform```, ```platform_family```, ```platform_version``` and ```kernel.machine``` are correct

Chef Client support implies Ohai support.

### Tier 1 Support

Tier 1 supported platforms are those for which Chef builds native binary "Omnitruck" (full-stack installer) packages. For each platform, there is equipment in the CI pipeline to perform client verification tests on machines of that platform.

Platform | Versions | Architectures | Package Format | Built on 
--- | --- | --- | --- | ---
CentOS | 5, 6, 7 | i386, x86_64 | rpm | RHEL 5
FreeBSD | 9, 10 | i386, amd64 | pkg_add pkg | FreeBSD 9
Mac OS X | 10.6, 10.7, 10.8, 10.9 | x86_64 | dmg | Mac OS 10.7
Oracle Enterprise Linux | 5, 6, 7 | i386, x86_64 | rpm | RHEL 5
Red Hat Enterprise Linux | 5, 6, 7 | i386, x86_64 | rpm | RHEL 5
Solaris | 9, 10, 11 | sparc, x86 (10 and 11 only) | shar | Solaris 9
Windows | 2003R2, 2008, 2008R2, 2012, 2012R2 | x86 and x86_64 | msi | Windows 2008R2
Ubuntu Linux | 10.04LTS, 12.04LTS, 14.04LTS | x86 and x86_64 | deb | Ubuntu 10.04LTS

### Tier 2 Support

Tier 2 supported platforms are those on which Omnitruck will serve packages, but those packages may not have been built on that OS variant. Additionally, we do no CVT on these platforms.

* SUSE Linux Enterprise Server 10, 11
* Scientific Linux 5.x, 6.x and 7.x (i386 and x86-64)
* Debian Linux 6.x and 7.x
* Gentoo Linux (rolling release)
* Arch Linux (rolling release)
* Fedora (current non-EOL revisions)
* OpenSUSE 12.3 (until EOL on 15 September 2014), 13.1

### Not Supported

"Not supported" means there may be code in-tree, but we don't build for and test on those platforms. We will take patches that don't break any tier 1 or tier 2 platforms, but we have no way of testing these.

* Solaris 8
* AIX 5.1L
* FreeBSD 8
* OpenBSD
* NetBSD
* Windows 2003, Windows 2000
* RHEL/CentOS/Oracle/Scientific 4.x or older
* HP-UX
* Mac OS X 10.5, older, or anything ppc-based

### Not Supported but We're Working On It

* AIX 6.1, 7.1 (ppc64)

### Not Supported but We'd be Open To It

* RHEL and SLES on POWER (ppc64)
* RHEL on System/z (would have to think long and hard though, how would we build clients?)

## Chef Server

Includes any of the add-ons (webui2/manage, push, etc.)

### Supported

* Ubuntu 10.04LTS, 12.04LTS, 14.04LTS
* RHEL 5.x and 6.x
* CentOS 5.x and 6.x
* Oracle 5.x and 6.x

### Unsupported

* Any other Linux or UNIX distributions
* Windows

## ChefDK

### Supported

* Windows 7, 8, 8.1
* RHEL 5.x, 6.x
* Mac OS X 10.9

### Unsupported

* Windows Vista, XP, 2000, ME, 98, 95, 3.11 for Workgroups
* Mac OS X < 10.9, anything ppc

## Appendix: Guiding Principles for Operating System Version Support

Once Chef Software, Inc. decides to support an operating system, we will also develop rules to determine under what upstream vendor lifecycle we will continue to support products, and they will be documented in this section. Vendors have various terminology to describe support lifecycles ('standard support', 'extended support', etc.) and it is useful to clarify what those mean in the context of Chef's products.

| Platform | Support Until | References
| Mac OS X | Current version, plus two previous versions | Apple does not clearly announce EOLs, so we have made this choice
| RHEL and EL-variants | End of RedHat Production 3 Phase | https://access.redhat.com/support/policy/updates/errata/
| Solaris | End of Premier Support | http://www.oracle.com/us/support/library/lifetime-support-hardware-301321.pdf
| Ubuntu | End of LTS lifecycle for LTS releases, end of standard release lifecycle for non-LTS releases | https://wiki.ubuntu.com/LTS
| Windows | End of Extended Support | https://support.microsoft.com/lifecycle/?c2=1163