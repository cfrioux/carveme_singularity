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
