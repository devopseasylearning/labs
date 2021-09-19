### create a user on all machines ( controller & all targets )

	useradd ansible -m -d /home/ansible -s /bin/bash

### add user to sudoers for root previliges  on all machines ( all targets )

	echo -e 'ansible  ALL=(ALL)  NOPASSWD:  ALL' > /etc/sudoers.d/ansible

### genereate ssh keys for above user on contrller machine 

```
	1) switch to user ( su - ansible )
	2) run "ssh-keygen" command as user ( this will genereate ssh keys for the user ) 
```
```
        on ansible controller machine
		cd /home/ansible/.ssh 
		cat id_rsa.pub (copy the content)
```
### copy user ssh keys from ansible contrller to all target hosts

```
	1) on all target machines
		   swith to the user ( su - ansible)
		   mkdir -p /home/jenkins/.ssh
		   touch /home/ansibles/.ssh/authorized_keys
		   chmod -R 700 /home/ansible/.ssh
		   vi /home/ansible/.ssh/authorized_keys  (enter the copied contet of id_rsa.pub from controller & save the file)
```	
	

