# ansible-role-nft

NFT bases firewall for 'servers'

# Supported distro's

- Debian 10.x, 11.x, possibly 9.x
- Ubuntu 20.x (todo)
- RedHat/CentOS 7.x, 8,x (todo)

# TODO:

- Install nft
- Optionally disable iptables / firewalld / ufw / whatever other firewall
- Configure nft to run at boot
- Trigger nft reload ( uncomment notify / add handler )

# Variables

trusted: list of machines / subnets to allow ssh traffic from

openports: tcp ports to open up to the public

nft_defines: list of custom groups and their subnets, to be used in custom rules

wireguard_port: if defined, open this udp port

nft_allow_http: if true, open ports http+https to the world

Default chain policies:

    nft_policy_input:       "drop"
    nft_policy_forward:     "accept"
    nft_policy_output:      "accept"
    nft_policy_prerouting:  "accept"
    nft_policy_postrouting: "accept"

On a per (ansible) host and group basis, custom rules can be defined

group_nft_input: []
group_nft_forward: []
group_nft_output: []

host_nft_input: []
host_nft_forward: []
host_nft_output: []

group_nft_postrouting: []
host_nft_postrouting: []
group_nft_prerouting: []
host_nft_prerouting: []

