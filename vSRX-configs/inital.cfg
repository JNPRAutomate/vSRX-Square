configure
delete security policies
delete security screen
delete security zones security-zone untrust
delete security zones security-zone trust
set interfaces ge-0/0/0.0 description "Vagrant Host Interface"
set interfaces ge-0/0/1.0 description "Client Interface"
set interfaces ge-0/0/2.0 description "Server Interface"
set security zones security-zone client interfaces ge-0/0/1.0
set security zones security-zone client interfaces ge-0/0/1.0 host-inbound-traffic system-services ping
set security zones security-zone client interfaces ge-0/0/1.0 host-inbound-traffic system-services traceroute
set security zones security-zone server interfaces ge-0/0/2.0
set security zones security-zone server interfaces ge-0/0/2.0 host-inbound-traffic system-services ping
set security zones security-zone server interfaces ge-0/0/2.0 host-inbound-traffic system-services traceroute
set security policies from-zone client to-zone server policy AllowAll match source-address any destination-address any application any
set security policies from-zone client to-zone server policy AllowAll then permit
set security policies from-zone server to-zone client policy AllowAll match source-address any destination-address any application any
set security policies from-zone server to-zone client policy AllowAll then permit
commit and-quit
