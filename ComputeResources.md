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
The queue consists of 18 nodes and 72 Nvidia GPUs.

1. 2 Nodes with 4 Nvidia NVIDIA L40S (44 GB memory) and 128 Intel Cores (256 GB of memory)
   * argon-itf-bx43-02
   * argon-itf-bx43-03
1. 1 Node with 6 Nvidia A10 GPUs (22 GB memory) and 112 Intel Cores (128 GB of memory)
  * argon-itf-bx54-12
2. 2 Nodes with 8 Nvidia 2080 TI GPUs and 80 Intel Cores (16 Total GPUs)
  * argon-itf-bx54-34
  * argon-itf-bx54-35
3. 7 Nodes with 4 Nvidia 1080 Ti GPUs and 40 Intel Cores (28 Total GPUs) (Good Single Precision GPU Performance)
  * argon-itf-ca37-12
  * argon-itf-ca37-15
  * argon-itf-ca37-18
  * argon-itf-ca37-21
  * argon-itf-ca37-24
  * argon-itf-ca37-27
  * argon-itf-ca37-30
4. 1 Node with 4 Titan V GPUs and 40 Intel Cores (Good Single and Double Precision GPU Performance)
  * argon-itf-ca38-39
5. 5 Nodes with 2 Nvidia P100 GPUs and 56 Cores (10 Total GPUs) (Good Single and Double Precision GPU Performance)
  * argon-lc-g11-35
  * argon-lc-g11-36
  * argon-lc-g11-37
  * argon-lc-g11-38
  * argon-lc-h21-40

## Schnieders Lab managed "IVRVOLTA" Queue 

1. 4 nodes with 1 Titan V GPU each and 64 GB of memory
  * argon-lc-f14-27
  * argon-lc-f14-28
  * argon-lc-f14-29
  * argon-lc-f14-30

This data was retrieved on Sept 10, 2024 using a command suggested by Glenn Johnson: qstat -s r -F -q $(qselect -q MS) 


