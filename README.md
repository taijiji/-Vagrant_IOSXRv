# Vagrant Cisco IOSXRv

# Download IOSXRv
1. get Cisco ID and Key for IOSXRv beta.
  https://xrdocs.github.io/getting-started/steps-download-iosxr-vagrant
1. add vagrant box

```
$ BOXURL="https://devhub.cisco.com/artifactory/appdevci-release/XRv64/latest/iosxrv-fullk9-x64.box"

$ curl -u YOUR-CCO-ID:YOUR-API-KEY $BOXURL --output ./iosxrv-fullk9-x64.box
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 1690M  100 1690M    0     0  2748k      0  0:10:29  0:10:29 --:--:-- 4876k

$ vagrant box add iosxrv ./iosxrv-fullk9-x64.box
```

```
$ vagrant box list

IOS-XRv                              (virtualbox, 0)
```

# Make Vagrantfile

```
$ vagrant init
```

```
$ vi Vagrantfile


# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :iosxrv1 do |iosxrv1|
    iosxrv1.vm.box = "IOS-XRv"
  end
end
```

# Build

```
$ vagrant up

...

$ vagrant status

Current machine states:

iosxrv1                   running (virtualbox)
```

# Access and login

```
$ ssh -p 2223 vagrant@localhost

Password: vagrant # default

RP/0/RP0/CPU0:ios#

RP/0/RP0/CPU0:ios#show version
Tue Jan 16 19:34:36.098 UTC

Cisco IOS XR Software, Version 6.2.1.23I
Copyright (c) 2013-2016 by Cisco Systems, Inc.

Build Information:
 Built By     : jwu
 Built On     : Mon Nov 21 00:33:58 PST 2016
 Build Host   : iox-ucs-005
 Workspace    : /auto/iox-ucs-005-san1/nightly/xr-dev_16.11.20C/iosxrv-x64
 Version      : 6.2.1.23I
 Location     : /opt/cisco/XR/packages/

cisco IOS XRv x64 () processor
System uptime is 8 minutes
```

# Reference
- [XR toolbox, Part 1 : IOS-XR Vagrant Quick Start](https://xrdocs.github.io/application-hosting/tutorials/iosxr-vagrant-quickstart)