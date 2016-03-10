# Open vStorage

Open vStorage is an open-source software defined storage platform on top of Ethernet drives (Seagate Kinetic), object storage or a pool of traditional SATA drives.
It allows anyone to create a storage system completely to his needs where performance and capacity can scale independently.
The core building blocks of the platform are distributed by nature and allow for a shared nothing architecture.

The different services can be categorized under 3 main components, the "Open vStorage Framework", "Open vStorage Volumedriver" and "Open vStorage Backend".
Depending on how and where these components and its sub-components get installed on any x86 hardware the Open vStorage platform can result
in a 'hyper-converged', 'hyper-scale' or 'geo-scale' storage system.

## Open vStorage Framework
The [Framework](https://github.com/openvstorage/framework) is the comfort layer offering the user an intuitive web based graphical user interface to configure and manage the storage system.
It offers functionality for easy integration with OpenStack Cinder and VMware vSphere, it provides an easy to use API to interact with the
distributed Open vStorage system, runs scheduled maintenance tasks, etc...

## Open vStorage Volumedriver
The [volumedriver](https://github.com/openvstorage/framework) offers the block interface to the storage consumer(like a hypervisor).
It's basically translating blocks into time aggregated objects which are stored in a Object storage system. It caches reads and buffers writes and is highly customizable to
tune the block layer to your specific needs, both on vPool and vDisk level.
It's written in C++.

## Open vStorage Backend
From Open vStorage perspective a "backend" is an object storage systems like Amazon S3, Openstack Swift, HGST Active Arhive System or others.
The Open vStorage alternative to these backends is an object storage system written in Ocaml developed under the codename [Alba](https://github.com/openvstorage/alba)
Alba turns commodity x86 storage servers into an always consistent distributed object storage systems.

## Getting started

Check our gitbooks on [how to get started with an installation](https://openvstorage.gitbooks.io/openvstorage/content/Installation/index.html).

## Nightly tests

A view on the different sets of Nightly test runs can be found [here](http://testrail.openvstorage.com/index.php?/runs/overview/10).
Email address ovs-guest@openvstorage.com with password 0vsgu3st should allow you to login and view the results

## Support

* For community support, please visit our [community support forum](https://groups.google.com/forum/#!forum/open-vstorage)
* For commercial support, please [contact Open vStorage](https://www.openvstorage.com/en/#footer)
