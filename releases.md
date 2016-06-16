# Open vStorage Release Notes

The current stable release is **Eugene**. The latest daily code changes are packaged and can be installed using our unstable package repository.
The under development release is **Fargo**

## Fargo (Under development)
* Release Name: Fargo
* Release Type: -
* Release Date: Planned for End Aug 2016
* Status: Under development

#### Version of the different packages:
* Not applicable yet.

#### Content
##### NC-ECC presets (global and local policies)
 NC-ECC (Network Connected-Error Correction Code) is an algorithm to store SCOs safely in multiple datacenters. It consists out of a global, across datacenter preset and multiple local, within a single datacentr presets.
 The NC-ECC algorithm is based on forward error correction codes and is further optimized for usage with a multi-datacenter approach. When there is a disk or node failure, additional chunks will be created using only data from within the same
datacenter. This ensures the bandwidth between datacenters isn’t stressed in case of a simple disk failure.

##### Open vStorage Edge
The OPen vStorage Edge is a light weight block driver which can be installed on Linux hosts and connect with the VolumeDriver over the network (TCP-IP or RDMA).

##### Performance optimized Volume Driver
By limiting the size of the metadata, the volume metadata now fits completely in RAM. The keep the metadata at an absolute minimum the deduplication was removed.
The Volume Driver uses a (networked) shared memory server architecture to avoid multiple copies in the datapath.

##### Multi-level ALBA
The ALBA backend now supports different levels. An all SSD ALBA backend can be used as performance layer in front of the capacity tier. Data is removed from the cache layer using a Least Recently Used (LRU) strategy. Additionally ALBA supports RDMA next to TCP-IP.

##### Multiple ASDs per device
For low latency devices adding multiple ASDs per device might provide a higher bandwidth to the device.

##### Additional supported interfaces
Open vStorage now supports next to the NFS & FUSE interface also blktap, Flocker and iSCSI as interface.

##### Multi-datacenter GUI
The GUI is adjusted to better highlight clusters which are spread across multiple sites.

##### Tag based domains
The failure domain concept has been replaced by tag based domains. ASD nodes and storage routers can now be tagged with one or more tags. Tags can be used to identify a rack, site, power feed, etc.

##### ETCD
ETCD is used to store the configuration settings for all components.

##### Logs and statistics to Redis
Logs and statistics are now pushed on to a Redis queue. The Redis queue can be popped to retrieved the values and allows to be easily integrated with standard monitoring tools.

##### Support for Ubuntu 16.04
Ubuntu 16.04 is now supported.

## Release History

### Eugene (Jan 12 2016)
* Release Name: Eugene
* Release Type: Major Update
* Release Date: Jan 12 2016
* Status: Available

#### Version of the different packages:
* open vstorage: 2.6.1-eugene-updates
* volumedriver: 5.6
* alba: 0.8
* arakoon: 1.8
* framework-alba-plugin: 1.6.1-eugene-updates
* alba asd manager: 1.5.1-eugene-updates

#### Content
##### Remove Node
Open vStorage allows for nodes to be removed from the Open vStorage Cluster. With this functionality you can remove any node and scale your storage cluster along with your changing storage requirements. Both active and broken nodes can be consistently removed from the cluster.

##### Policy Update
Open vStorage enables you to actively add, remove and update policies for specific ALBA backend presets. Updating active policies might result in Open vStorage to automatically rewrite data fragments.

##### ALBA Backend Encryption
When configuring a backend presets, AES-256 encryption algorithms can be selected.

##### Failure Domain
A Failure Domain is a logical grouping of Storage Routers. The Distributed Transaction Log (DTL) and MetaDataServer (MDS) for Storage Router groups can be defined in the same Failure Domain or in a Backup Failure domain. When the DTL and MDS are defined in a Backup Failure Domain, data loss in case of a non-functioning Failure Domain is prevented. Defining the DTL and MDS in a backup Failure Domain requires low latency network connections.

##### Distributed Scrubber
Snapshots which are out of retention period are indicated as garbage and removed by the Scrubber. With the Distributed Scrubber functionality you can now decide to run the actual scrubbing process away from the host that holds the volume. This way, hosts that are running Virtual Machines do not experience any performance hit when the snapshots of those Virtual Machines are scrubbed.

##### Scrubbing Parent vDisks
Open vStorage allows to create clones of vDisks. The maximal depth of the clone tree is limited to 255. When a clone is created, scrubbing is still applied to the actual parent of the clone.

##### New API calls
Following API's are added:
* vDisk templates (set and create from template)
* Create a vDisk (name, size)
* Clone a vMachine from a vMachine Snapshot
* Delete a vDisk
* Delete a vMachine snapshot
These API calls are not exposed in the GUI.

##### Removal of the community restrictions
The ALBA backend is no longer restricted and you are no longer required to apply for a community license to use ALBA. The cluster needs to be registered within 30 days otherwise the GUI will stop working until the cluster is registered.

##### Some smaller Feature Requests were added also:
* Removal of the GCC dependency.
* Option to label a manual snapshot as ‘sticky’ so it doesn’t get removed by the automated snapshot cleanup.
* Allow stealing of a volume when no Hypervisor Management Center is configured and the node rowning the volume  is down.
* Set_config_params for vDisk no longer requires the old config.
* Automatically reconfigure the DTL when DTL is degraded.
* Automatic triggering of a repair job when an ASD is down for 15 minutes.
* ALBA is independent of broadcasting.
* Encryption of the ALBA socket communication.
* New Arakoon client (pyarakoon).

##### Following are the most important bug fixes in the Eugene release:
* Fix for various issues when first node is down.
* "An error occurred while configuring the partition" while trying to assign DB role to a partition.
* Cached list not updated correctly.
* Celery workers are unable to start.
* Nvme drives are not correctly detected.
* Volume restart fails due to failure while clearing the DTL.
* Arakoon configs not correct on 4th node.
* Bad MDS Slave placement.
* DB role is required on every node running a vPool but isn't mandatory.
* Exception in tick crashes the ovs-scheduled-task service.
* OVS-extensions is very chatty.
* Voldrv python client hangs if node1 is down.
* Bad logic to decide when to create extra alba namespace hosts.
* Timeout of CHAINED ensure single decorator is not high enough.
* Possibly wrong master selected during "ovs setup demote".
* Possible race condition when adding nodes to cluster.


### Denver (Nov 18 2015(

* Release Name: Denver
* Release Type: Major Update
* Release Date: Nov 18 2015
* Status: Available


#### Content
##### New repo structure
The new repo location is apt.openvstorage.org (deb) and yum.openvstorage.org (rpm). Note that we now only support name based releases and no longer have different quality levels (alpha, beta, …). The latest changes can be found on unstable.

##### Failure Domains
The Failure Domains functionality allows to group Storage Routers together based upon their location and allows to configure the MetaDataServer based upon this grouping. In the next release the Failure Domain configuration will also take the Distributed Transaction Log (DTL) into account. This will allow to make sure that when there is a site disaster, the data in the DTL can be safeguarded to prevent dataloss.

##### Updater
The Open vStorage updater now also supports rpms.

##### Generic ASD parameters
An option was added to specify generic configuration parameters for ASDs f.e. the multicast period.

The Denver release also contains following bugfixes:
* Failure to start the distributed backend due to config files not being distributed correctly.
* Bug which prevented to remove ASDs from a node when the node was unavailable.
* Bugfix for incorrect locking of the vDisks events.
* The VMware deploy script now adds all disks to the Storage Router VM.
* Sync_with_mgmtcenter logs ERROR when the vdisk is not attached to a VM.
* Update of ovs-snmp to make sure Open vStorage Backends can be monitored.
