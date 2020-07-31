# Port forwarding for CPE NAT IP

**This hook will not work on Bonding 6.6 or above. Please see the "Firewall
Management" section of the Bonding documentation for a port forwarding example
that works on Bonding 6.6 and above.**

This is an example hook to allow port forwarding to hosts on a private
connected IP range with a CPE NAT IP defined.

To use, get the ID of the CPE NAT IP from the web interface and save the file
under `/etc/bonding/cpenatip.d/<cpenatip_id>/` on the bonder. Then run
`service bonding restart` to restart bonding and load the hook.
