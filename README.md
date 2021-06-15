# carveme_singularity
SIngularity image definition to install Cplex and Carveme in a container (e.g. for using the software on a cluster)

## Installation
The binary file of Cplex (under license) has to be located in the same directory as the definition file. 

```
directory
├── carveme.def
│
├── cplex_studio128.linux-x86-64.bin
````

Depending on the version of Cplex you use you might need to change the name in the definition file. Here it is version 12.8.

The image is build with the following command:


```sh
sudo singularity build singularity.sif singularity.def
```

```carveme_2.def``` is another version of the image starting directly from the *ibmjava:latest* docker image

If you have issue when using the container on a cluster, you can try these options:

```sh
singularity run -c -B /folder/cluster/:/folder/cluster/ /folder/cluster/carveme.sif carve /folder/cluster/input_folder/data.faa
```

The ``-B`` option gives access to the Singularity container to a specific path. The first path corresponds to the local/cluster path and the second path (after the ``:``) corresponds to the path inside the Singularity container. Using this option can solved issue with error message ``Unable to create output folder: /folder/cluster/input_folder`` (because the Singularity container has no right to create output files in the folder).

The ``-c`` option runs the Singularity image in an isolated manner with a minimal /dev and empty other directories (e.g. /tmp and $HOME) instead of sharing filesystems from your host. This avoids issue with environment present in the cluster. Using this option can solved issue with error message ``Segmentation fault`` after Diamond.
