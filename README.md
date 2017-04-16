# Flexible Linux VM Scale Set + Head Node / NFS Server
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmkiernan%2FFlexHPC%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Fmkiernan%2FFlexHPC%2Fmaster%2FRawANSYSCluster%2Fazuredeploy.json" target="_blank">
<img src="http://armviz.io/visualizebutton.png"/>
</a>
<br><br>

<b>Quickstart</b>

	1) Deploy ARM Template
		a. Click on the link above
		b. Select HPC available region
		c. Select vm size (H16m/H16mr or A8/A9) and quantity (make sure to have quota for it)
		d. Name your user account - this is the account you will login and run jobs with.
		e. Manually upload and configure your data + software on /share/data 
		f. Configure any license server required. 
		g. Run your Job
	2) Customize
		a. Clone this template into your own github. 
		b. Edit the cn-setup.sh to install any additional software you need. 

<b>Architecture</b>

<img src="https://github.com/tanewill/5clickTemplates/blob/master/images/hpc_vmss_architecture.png"  align="middle" width="395" height="274"  alt="hpc_vmss_architecture" border="1"/> <br></br>

This template deploys a Linux VM Scale Set (VMSS) along with a Head Node (+ NFS server in the same VM) in the same virtual network. You can connect to the headnode via the public IP address, then connect from there to VMs in the scale set via private IP addresses. To ssh into the jumpbox, use the following command:

ssh {username}@{jumpbox-public-ip-address}

To ssh into one of the VMs in the scale set, go to resources.azure.com to find the private IP address of the VM, make sure you are ssh'ed into the jumpbox, then execute the following command:

ssh {username}@{vm-private-ip-address}

You will also find the private IP addresses in /share/home/username/bin/nodeips.txt

Note: VM scaleset overprovisioning is disabled in this version for now. 

<b>Adding & Removing Nodes</b>

TBD. 


<i>Credit: Taylor Newill & Xavier Pillons for base templates.</i>
