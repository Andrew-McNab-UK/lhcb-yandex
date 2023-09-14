# lhcb-yandex

To run LHCb jobs on Yandex Cloud with these scripts you need to create
two types of VMs: worker nodes (WN) and squid caches. You need about 3 squid
cache instances and the workers auto-discover the squid VM IPs through the
Yandex APIs.

Both both types you copy the files to a new VM with the
*-copy-snapshot-files script and then ssh to the VM and run the
*-prepare-snapshot file that has been copied there.

Once the snapshot script has been run, you need to make a snapshot using the
Yandex web dashboard. These can be run automatically using the Yandex
autoscaling. You want to have constant levels of both types of VM. The VMs
periodically shut themselves down and respawn to pick up new versions etc.
