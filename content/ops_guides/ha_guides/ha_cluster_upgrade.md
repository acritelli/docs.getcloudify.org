---
title: Cloudify High Availability Cluster Upgrade Guide
category: Cluster Upgrade
draft: false
weight: 100
---

### Upgrading a Cloudify Compact Cluster (3 nodes)

If the initial cluster installation was done using the Cloudify Cluster Manager, follow this simplified process.
Updating a Cloudify compact cluster leveraging the Cloudify Cluster Manager
You can use the Cloudify Cluster Manager tool to upgrade a compact cluster: 

Upgrade your Cloudify Cluster Manager by running 

        sudo yum install -y <Cloudify Manager Installation RPM>

On the host that has Cloudify Cluster Manager installed, run cfy_cluster_manager upgrade. 

Optional Arguments: 

        --config-path The completed cluster configuration file path. Default: ./cfy_cluster_config.yaml
        --upgrade-rpm Path to a v6.1.0 cloudify-manager-install RPM. This can be either a local or remote path.

        Default:<Cloudify Manager Installation RPM>

        -v, --verbose Show verbose output

Running this command will automatically run the upgrade procedure on the cluster. 

If the Cluster was manually deployed, please follow this procedure instead:

###Manually updating a Cloudify compact cluster

Install the new 6.1.0 cloudify-manager-install RPM on all 3 nodes of the cluster, by using the command: 

        sudo yum install -y <Cloudify Manager Installation RPM>

Repeat this step on all 3 nodes.

On each of the cluster nodes, run  cfy_manager upgrade -c <path to DB config>. 

Do it one after the other, not in parallel.

        Tip: If you used the cloudify-cluster-manager tool to generate the Cloudify cluster, the path to the DB config file is /etc/cloudify/postgresql-<node number>_config.yaml.
        
If the cluster was manually installed, please direct the command to the path of the file you generated.


On each of the cluster nodes, run  cfy_manager upgrade -c <path to rabbitmq config>. 
Do it one after the other, not in parallel.

        Tip: If you used the cloudify-cluster-manager tool to generate the Cloudify cluster, the path to the RabbitMQ config file is  /etc/cloudify/rabbitmq-<node number>_config.yaml. If the cluster was manually installed, please direct the command to the path of the file you generated.


On each one of the cluster nodes, run  cfy_manager upgrade -c <path to manager config> 
Do it one after the other, not in parallel.

        Tip: If you used the cloudify-cluster-manager tool to generate the Cloudify cluster, the path to the manager config file is /etc/cloudify/manager-<node number>_config.yaml. If the cluster was manually installed, please direct the command to the path of the file you generated. 


If Cloudify agents are used in your deployments, run the following command from just one of the cluster nodes:
cfy agents install


When opening the Cloudify Management Console after the upgrade, you might see “This page is empty”, this happens because of cached data. To solve this, press CTRL + Shift + R.
 
## Upgrading a Cloudify Fully Distributed Cluster (9+ nodes)
        
If the initial cluster installation was done using the Cloudify Cluster Manager, follow this simplified process.
Updating a Cloudify Fully Distributed Cluster leveraging the Cloudify Cluster Manager
You can use the Cloudify Cluster Manager tool to upgrade a fully distributed cluster: 

Upgrade your Cloudify Cluster Manager by running 
        
        sudo yum install -y <Cluster Manager Installation RPM>
        
On the host that has Cloudify Cluster Manager installed, run cfy_cluster_manager upgrade. 
Optional Arguments: 
        
        --config-path The completed cluster configuration file path. Default: ./cfy_cluster_config.yaml
        --upgrade-rpm Path to a v6.1.0 cloudify-manager-install RPM. This can be either a local or remote path.
        Default: <Cloudify Manager Installation RPM>
        
        -v, --verbose Show verbose output
	        Running this command will automatically run the upgrade procedure on the cluster. 

If the cluster was manually deployed, please follow this procedure instead:
        
Manually updating a Fully Distributed Cluster
Update steps:
Install the new 6.1.0 cloudify-manager-install RPM on all the cluster nodes, by using the command: 
        sudo yum install -y <Cloudify Manager Installation RPM> 
Repeat this step on all 9 nodes.


On all three database nodes run cfy_manager upgrade 
Do it one after the other, not in parallel.


On all three RabbitMQ nodes run cfy_manager upgrade
Do it one after the other, not in parallel.


On all manager nodes, run cfy_manager upgrade
Do it one after the other, not in parallel.


If Cloudify agents are used in your deployments, run the following command from just one of the manager nodes:
cfy agents install


When opening the Cloudify Management Console after the upgrade, you might see “This page is empty”, this happens because of cached data. To solve this, press CTRL + Shift + R.
