# Singularity recipe for Scipion

This repository contains a singularity definition file created to install scipion core and cryo-em plugins. This container can be executed to run scipion in single/master node or to send jobs to queue in a slurm based scheduled routine. 

# Executing singularity image

The Scipion singularity image can be executed as: 

singularity exec --nv --bind /usr/bin/sbatch:/usr/bin/sbatch:ro,/usr/bin/scancel:/usr/bin/scancel:ro,/usr/lib64/slurm:/usr/lib64/slurm:ro,/etc/slurm:/etc/slurm:ro,/usr/bin/munge:/usr/bin/munge:ro,/etc/munge:/etc/munge:ro,/usr/lib64/libreadline.so.7:/usr/lib64/libreadline.so.7:ro,/usr/lib64/libhistory.so.7:/usr/lib64/libhistory.so.7:ro,/usr/lib64/libtinfo.so.6:/usr/lib64/libtinfo.so.6:ro,/var/run/munge:/var/run/munge:ro,/usr/lib64/libmunge.so.2:/usr/lib64/libmunge.so.2:ro,/usr/lib64/libmunge.so.2.0.0:/usr/lib64/libmunge.so.2.0.0:ro,/run/munge:/run/munge:ro /path/to/sif/file /opt/scipion3

# Notes 
* this
