# debug-ansible-f5
A simple F5 tasks to debug slowness of `bigip_virtual_server` module

It contains 100 SSL certs and keys.

Note: Im my case, network latency between Ansible host and Virtual LTM is about 10ms.



It should be run in the following steps:

1. Update username and password (with Admin rights) in group_vars/all_devices/auth.yml
2. Put a correct F5 LTM hostname in inventories/testing/hosts

3. Run these playbooks

$ time ansible-playbook upload-certificates_and_keys.yml
$ time ansible-playbook run-nodes-pools-vs.yml



-----------
My Results:

$ time ansible-playbook upload-certificates_and_keys.yml

My results:
real	7m38.162s
user	2m0.576s
sys	0m41.232s

$ time ansible-playbook run-nodes-pools-vs.yml

real	18m22.430s
user	3m43.109s
sys	0m42.831s

$ time ansible-playbook run-nodes-pools-vs.yml --tags=vs

real	14m0.379s
user	2m36.049s
sys	0m21.154s
