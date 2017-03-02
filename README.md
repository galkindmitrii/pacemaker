pacemaker
=========

* VIPAbgp - An OCF resource for Pacemaker to announce a VIP via BGP:

- uses vtysh to anncounce/denounce addresse, no config rewrite/restart required;
- requires Quagga suite with basic configuration and peers defined;
- does not assign the VIP to interface itself, but default IPaddr2 resource and collocation constraint can be used for that:

Create VIPAbgp resource:

- pcs resource create VIPBGP ocf:heartbeat:VIPAbgp ip=192.168.100.100/32

Than create IPaddr2 resource:

- pcs resource create VIPIP ocf:heartbeat:IPaddr2 params ip=192.168.100.100

And their collocation:

- pcs constraint colocation add VIPBGP with VIPIP
