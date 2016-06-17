# Open vStorage

Open vStorage is an open-source software defined storage platform on top of Ethernet drives (Seagate Kinetic), object storage or a pool of traditional SATA drives.
It allows anyone to create a storage system completely to his needs where performance and capacity can scale independently.
The core building blocks of the platform are distributed by nature and allow for a shared nothing architecture.

The different services can be categorized under 3 main components, the "Open vStorage Framework", "Open vStorage Volumedriver" and "Open vStorage Backend".
Depending on how and where these components and its sub-components get installed on any x86 hardware the Open vStorage platform can result in a 'hyper-converged', 'hyper-scale' or 'geo-scale' storage system.

Open vStorage is licensed under the [AGPLv3 License](http://www.gnu.org/licenses/agpl.html).

# The Key Projects
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

## Other Repos
* [ALBA ASD Manager](https://github.com/openvstorage/alba-asdmanager): The ALBA ASD manager is a lightweight library which turns devices into disks which are addressable as key/value disk over an IP and port.
* [Arakoon](https://github.com/openvstorage/arakoon):The consistent distributed key-value store in Open vStorage.
* [Blktap](https://github.com/openvstorage/blktap): Open vStorage blktap tree.
* [Devops](https://github.com/openvstorage/dev_ops): Tools to automatically setup, manage and troubleshoot Open vStorage clusters.
* [Docker Arakoon](https://github.com/openvstorage/docker_arakoon): Arakoon build environment in docker.
* [Docker tools](https://github.com/openvstorage/docker-tools): Docker images and associated tools to run the OpenvStorage setup inside docker.
* [Framework ALBA Plugin](https://github.com/openvstorage/framework-alba-plugin): The Framework ALBA plugin extends the OpenvStorage GUI with functionality to manage ASDs (Alternate Storage Daemon) and Seagate Kinetic drives.
* [Framework Cinder Plugin](https://github.com/openvstorage/framework-cinder-plugin): Framework Cinder Plugin.
* [Framework Tools](https://github.com/openvstorage/framework-tools): The framework-tools repository contains tools for developers of the Open vStorage project.
* [GObjFS](https://github.com/openvstorage/gobjfs): The Open vStorage Ganesha Object FileSystem provides a flat object store to an ASD.
* [Integrationtests](https://github.com/openvstorage/integrationtests): Open vStorage automated integration tests.
* [Openvstorage Flocker Driver](https://github.com/openvstorage/openvstorage-flocker-driver): OpenvStorage Block Device driver for Flocker, a container data orchestration system.
* [Openvstorage Health Check](https://github.com/openvstorage/openvstorage-health-check): The health check is classified as a monitoring, detection and healing tool for Open vStorage.
* [openvstorage-log-consolidation](https://github.com/openvstorage/openvstorage-log-consolidation): Automated installation of kibana / logstash log consolidation for Open vStorage.
* [Open vStorage Monitoring](https://github.com/openvstorage/openvstorage-monitoring) Monitoring scripts which push logs and statistics to Redis and from Redis to InfluxDB and ELK
* [Pyrakoon](https://github.com/openvstorage/pyrakoon): An alternative Python client for Arakoon.
* [Qemu](https://github.com/openvstorage/qemu): Open vStorage Qemu tree.
* [TGT](https://github.com/openvstorage/tgt): iSCSI target driver (TGT) for Open vStorage.
* [OVS Documentation](https://github.com/openvstorage/ovs-documentation): The Open vStorage Administration Guide.
* [Volumedriver buildtools](https://github.com/openvstorage/volumedriver-buildtools): Scripts and (modified) thirdparty code required to build the Open vStorage VolumeDriver.

# Getting started - Documentation
The documentation Open vStorage is split into different GitBooks:
* [Open vStorage Administration](https://openvstorage.gitbooks.io/openvstorage/content/)
* [Open vStorage Framework Internals](https://openvstorage.gitbooks.io/framework/content/)
* [Open vStorage VolumeDriver Internals](https://openvstorage.gitbooks.io/volumedriver/content/)

A quick starting guide can be found [here](https://openvstorage.gitbooks.io/openvstorage/content/Installation/index.html). The above links are  pointing to the documentation for the latest version. Documentation for previous versions can be found [here](https://openvstorage.gitbooks.io/openvstorage/content/olderreleases.html).

# Release Notes
The release notes for the different Open vStorage releases can be found [here](releases.md).


# Nightly tests

A view on the different sets of Nightly test runs can be found [here](http://testrail.openvstorage.com/index.php?/runs/overview/10).
Email address ovs-guest@openvstorage.com with password 0vsgu3st should allow you to login and view the results

# Community

[Openvstorage.org](http://www.openvstorage.org) is our community website.
If you feel like contributing, don't hesitate to do so, [here](CONTRIBUTING.md) you can find some info/guidelines

