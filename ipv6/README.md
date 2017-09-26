These hooks facilitate setting up addressing and routing for IPv6 on bonding
tunnels and connected IPs.

Usage
-----

Hooks can be used by being configured appropriately and installed to
`/etc/bonding/tun.d/`. Each hook should be configured by supplying appropriate
values to the variables near the top of each file.

For aggregators, the variables are:

 - `BOND_TUNNEL_LOCAL_IPV6`
 - `BOND_TUNNEL_PEER_IPV6`
 - `BOND_TUNNEL_DELEGATED_IPV6`

For bonders, the variable are:

 - `BOND_TUNNEL_LOCAL_IPV6`
 - `BOND_TUNNEL_PEER_IPV6`
 - `BOND_TUNNEL_DELEGATED_IPV6`
 - `BOND_CONNECTEDIP_IPV6`
 - `BOND_CONNECTEDIP_INTERFACE`

Each hook should be installed in the directory
`/etc/bonding/tun.d/<tunnel_id>/` on its node type and be made executable. For
example, given bond 123, on the aggregator, copy "aggregator-tun-ipv6-hook" to
`/etc/bonding/tun.d/123/ipv6`, and on the bonder, copy "bonder-tun-ipv6-hook"
to the same path. The hook files on both machines should be made executable.

The `radvd` package should be installed on the bonder.
