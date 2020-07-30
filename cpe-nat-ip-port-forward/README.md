# Port forwarding for CPE NAT IP

**This hook will not work on Bonding 6.6 or above. Please see the "Firewall
Management" section of the Bonding documentation for a port forwarding example
that works on Bonding 6.6 and above.**

This is an example firewall hook to allow port forwarding to hosts on a
private connected IP range with a CPE NAT IP defined.

To use, save the file under `/etc/firewall.d/` on the bonder and run
`service firewall restart` to apply.
