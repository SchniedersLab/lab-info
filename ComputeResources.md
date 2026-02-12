# Getting started with U. of Iowa computing resources

## The University of Iowa Argon Cluster
* Please request an [account here](https://research.its.uiowa.edu/our-services/computing-services/argon-high-performance-computing-hpc).
* Argon instructions are available via [Argon Cluster](https://wiki.uiowa.edu/display/hpcdocs/Argon+Cluster).
* There are also more general [Cluster Systems Documentation](https://wiki.uiowa.edu/display/hpcdocs/Cluster+Systems+Documentation).

## The Schnieders' Lab Dedicated Storage
* When logged into the Argon cluster, our lab's dedicated storage is located at /Dedicated/schnieders
* It can also be mounted locally on your Mac from within Finder using "Connect to Server" and the address: smb://lc-rs-storage19.hpc.uiowa.edu/schnieders
* General information about large scale storage at the U. of Iowa is available here [Large Scale Storage Service Documentation](https://its.uiowa.edu/lss).

## Schnieders Lab "MS" Queue
The queue consists of 6 nodes and 34 Nvidia GPUs.

1. 2 Nodes with 4 Nvidia NVIDIA L40S (44 GB memory) and 128 Intel Cores (256 GB of memory)
   * argon-itf-bx43-02
   * argon-itf-bx43-03
2. 1 Node with 6 Nvidia A10 GPUs (22 GB memory) and 112 Intel Cores (128 GB of memory)
  * argon-itf-bx54-12
3. 2 Nodes with 8 Nvidia 2080 TI GPUs and 80 Intel Cores (16 Total GPUs)
  * argon-itf-bx54-34
  * argon-itf-bx54-35
4. 1 Node with 4 Nvidia 1080 Ti GPUs and 80 Intel Cores
  * argon-itf-bx51-13

This data was retrieved on Feb 12, 2026 using a command suggested by Glenn Johnson: qstat -s r -F -q $(qselect -q MS) 


