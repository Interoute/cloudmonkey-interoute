# cloudmonkey-interoute

This is a fork of the Cloudmonkey command line interface, modified for use with the [Interoute Virtual Data Centre](http://cloudstore.interoute.com/main/WhatInterouteVDC).

The modification required is to handle API access to the different VDC regions (Europe, USA, Asia). This is implemented using a new configuration variable `region`.

The default value is 'europe'. Note that the master version of Cloudmonkey can access the default region without modification.

See the original repo here: [cloudstack-cloudmonkey](https://github.com/apache/cloudstack-cloudmonkey)

## Modifications

The files `cloudmonkey.py`, `requester.py` and `config.py` have been modified. To access the Asia or USA region, add a line to the Cloudmonkey `config` file in the `[server]` section:

    region = asia

or 

    region = usa

(the region name is not case sensitive). You can also change this interactively while Cloudmonkey is running:

    set region usa


## How to install this modified version

You can make a fresh install of this modified version of Cloudmonkey using the `pip` command:

    sudo pip install git+https://github.com/Interoute/cloudmonkey-interoute.git

Or to upgrade an existing installation:

    sudo pip install --upgrade git+https://github.com/Interoute/cloudmonkey-interoute.git

This version of Cloudmonkey may not work with other cloud computing providers that use the same API. So be careful if you use Cloudmonkey with several providers.

(This version adds a new parameter input ('region=europe') to every API call. API servers generally ignore any parameters that are not recognised, however if the server is programmed to do validity checking then Cloudmonkey may not work.)
