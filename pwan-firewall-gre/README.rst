Private WAN router space hook
==============================

This hook facilitates setting up custom BIRD BGP configuration and GRE tunnels to
remote firewalls on a private WAN router for private WAN spaces.


Usage
------

#. This hook can be used by being configured appropriately and installing to
   ``/etc/bonding/privatewan-router-space.d/``. Private WAN router space hooks use
   the space key to specify the appropriate directory. For example, if
   ``example_hook`` should run for a space and its key is "abcdef", then the hook
   should be placed in the directory

   ::

        /etc/bonding/privatewan-router-space.d/abcdef/example_hook

#. Hooks must be marked as executable in order to be run.
   For example, if the script path was /etc/bonding/leg.d/all/example_hook, the
   command is:

   ::

        chmod +x /etc/bonding/privatewan-router-space.d/all/example_hook

#. This hook should be configured by supplying appropriate values to the
   following variables for each space:

   - ``GATEWAY``: ID of gateway peer
   - ``PWR_IP``: public IP of private WAN router
   - ``GATEWAY_IP``: public IP of gateway peer
   - ``LOCAL_GRE_IP``: local IP of GRE
   - ``REMOTE_GRE_IP``: remote IP of GRE
   - ``LOCAL_AS``: local BGP AS
   - ``REMOTE_AS``: BGP AS of remote

   You will need a set of variables for each GRE to be set up by the hook. Each
   set should be defined in a different file called
   ``/etc/bonding/spaceprivatewan/<space_key>/<GATEWAY>``. For example, if
   GATEWAY=10 and the space key is "abcdef", then the file path should be

   ::

        /etc/bonding/spaceprivatewan/abcdef/10

   Here's an example of the file's contents:

   ::

        GATEWAY=10
        PWR_IP="19.9.9.9"
        GATEWAY_IP="17.7.7.7"
        LOCAL_GRE_IP="172.16.10.2"
        REMOTE_GRE_IP="172.16.10.1"
        LOCAL_AS="65000"
        REMOTE_AS="65001"

#. Create the custom config file for BIRD. Its contents will be auto-generated
   by the hook, but the file needs to exist.

   ::

        mkdir -p /etc/bonding/bird
        touch /etc/bonding/bird/custom-external-bird.conf

#. If the space’s key is updated in the management server, the hook and variable
   directories for this space must be manually renamed to reflect the new key.
#. After a space hook has been added, you must restart the space from the
   management server to execute the hook for the first time.

