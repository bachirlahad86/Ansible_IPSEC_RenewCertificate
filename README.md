# Ansible_IPSEC_RenewCertificate
Using Ansible to renew certificates on thousands of Cisco IOS spokes


## Steps required for execution

1. Update the spokes IPs in the inventory file *invent.yml* like: <br />
all: <br />
&nbsp;hosts: <br />
&nbsp;&nbsp;10.x.x.x: <br />
&nbsp;&nbsp;10.x.x.x: <br />
&nbsp;&nbsp;10.x.x.x: <br />
2. Run the Ansible playbook:<br /> **ansible-playbook -i invent.yml play.yml** <br />
The playbook will be running a batch of 50 hosts at a time from the hosts available in the inventory file.
3. Failed connections to spokes are logged into the *Failed_Connections.txt* file, you can rerun the ansible playbook with these connections once the connection is up.
4. Run the second Ansible playbook to collect the status of the Tunnel after around 10 min to make sure that the dmvpn status is accurate: **ansible-playbook -i invent.yml play1.yml**
5. Tunnel status for each spoke, after the certifications renewal, is logged into the *Tunnel_status.txt*. ( as example: IKE means that the tunnel still down even after the certifications renewal)
6. For more info regarding the output of a specific command or any error that occurred on a specific  spoke, you can check the folder/file *Logs/ Playbook.log*.
7. Do a backup for the results in Tunnel_status.txt. and Failed_Connections.txt after each playbook run.

















