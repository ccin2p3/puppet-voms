## cernops-voms puppet module

[![Puppet Forge](http://img.shields.io/puppetforge/v/lcgdm/voms.svg)](https://forge.puppetlabs.com/lcgdm/voms)
[![Build Status](https://travis-ci.org/cern-it-sdc-id/puppet-voms.svg?branch=master)](https://travis-ci.org/cern-it-sdc-id/puppet-voms)

This module manages VOMS resources for VOMS clients

VOMS is the Virtual Organization Membership Service, in use by gLite, EMI, and
other grid computing projects.

## Examples
### Client Examples

     voms::client{'MyVO':
        vo       => 'MyVO',
        servers  => [{server => 'voms.cern.ch',
                      port   => '15009',
                      dn     => '/DC=ch/DC=cern/OU=computers/CN=voms.cern.ch',
                      ca_dn  => '/DC=ch/DC=cern/CN=CERN Trusted Certification Authority'
                     },
                     {server => 'lcg-voms.cern.ch',
                      port   => '15009',
                       dn    => '/DC=ch/DC=cern/OU=computers/CN=lcg-voms.cern.ch',
                       ca_dn => '/DC=ch/DC=cern/CN=CERN Trusted Certification Authority'
                     }]

 The above declaration will create the files:

     /etc/vomses/MyVO/voms.cern.ch
 and

     /etc/grid-security/vomsdir/MyVO/voms.cern.ch.lsc


 For some VOs, you can probably find a predefined class to enable a
 VO easily which does all the required setup without any 
 additional configuration e.g:

     class{'voms::atlas':}
     class{'voms::dteam':}

Additions of new VOs will be accepted, please submit pull requests
however zero validation of parameters will be made.

## Authors
 CERN IT/GT/DMS <it-dep-gt-dms@cern.ch>, Ricardo Rocha
 CERN IT/PS/PES <it-dep-ps-pes@cern.ch>, Steve Traylen
 Bugs, Comments, Pull requests - https://github.com/cernops/puppet-voms



