# Singularity recipe for Scipion

This repository contains a singularity definition file created to install scipion core and cryo-em plugins. This container can be executed to run scipion in single/master node or to send jobs to queue in a slurm based scheduled routine. 

# Configuring .def file 

Before to build the scipion image from the definition file, modify the .def file to set the path where the built image (.sif) file will be located.
You can to this by manually editing the .def file using a text editor and replacing the string /path/to/sif (line 97) by the correct absolute .sif path (ex: /opt/singularity_example.sif).
Alternatively you can use sed:
```console
sed -i 's#/path/to/sif#/path/example/sif#g' singularity_example.def
```
This change will affect the scipion hosts.conf file and scipion will be able to run call the scipion singularity image in its sbatch file

# Building the image 

To build the scipion image i.e. convert the definition .def file to the singularity image .sif file, please run the following command: 

```console
sudo singularity build --nv /path/to/singularity/.sif /path/to/singularity/.def
```

# Executing singularity image

The Scipion singularity image can be executed as (please change the .sif path if needed): 

```console
singularity exec --nv --bind /usr/bin/sbatch:/usr/bin/sbatch:ro,/usr/bin/scancel:/usr/bin/scancel:ro,/usr/lib64/slurm:/usr/lib64/slurm:ro,/etc/slurm:/etc/slurm:ro,/usr/bin/munge:/usr/bin/munge:ro,/etc/munge:/etc/munge:ro,/usr/lib64/libreadline.so.7:/usr/lib64/libreadline.so.7:ro,/usr/lib64/libhistory.so.7:/usr/lib64/libhistory.so.7:ro,/usr/lib64/libtinfo.so.6:/usr/lib64/libtinfo.so.6:ro,/var/run/munge:/var/run/munge:ro,/usr/lib64/libmunge.so.2:/usr/lib64/libmunge.so.2:ro,/usr/lib64/libmunge.so.2.0.0:/usr/lib64/libmunge.so.2.0.0:ro,/run/munge:/run/munge:ro /opt/images/scipion_singularity.sif /opt/scipion3
```

# Notes 
* The singularity execution command above uses a bind flag to allow the container to have access to the slurm binaries, libraries and dependencies. This will be simplified in the future.  

