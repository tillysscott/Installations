# Code tips
## Markdown tips:
- help page: [here](https://code.visualstudio.com/docs/languages/markdown)  
    - Use pop up bubble choose plain text or mark down link
    - put 4 spaces before dash for more indent  

![image desc](./Screenshot%202025-06-03%20102209.png)  
[text description of link](#how-to-transfer-data-from-maxwell-directly-to-the-team-drive)
- ctrl + shift + v for md preview
- drag tab to right to open preview side-by-side window
- right click on window, open in brower then save as pdf to export this document

## HPC tips
- `seff $jobid` time and memory etc. of finished job
- `readlink -f file` get real location of symbloic linked file
- `source /opt/software/uoa/apps/miniconda3/latest/etc/profile.d/conda.sh` source miniconda3 installation
    - use within scripts to be able to load a conda environment
- sometimes the HPC will take the local python version rather than the conda environement version, use `unset PYTHONPATH` to force it to use conda version. Pychopper requies python v.3.10, and local copy was v.3.9

### How to transfer data from Maxwell directly to the team drive  
- All outputs have been tar zipped. Read below for description of these outputs  
- First log into Maxwell (or Macleod) as normal  
- Navigate to the directory you want to transfer to or from  
- On the command line do: 
```
smbclient '\\uoa.abdn.ac.uk\global' -D 'CLSM\CGEBM\Bioinformatics Unit\CGEBM Projects Bfx\<any project folder> 
```
Example: ``` smbclient '\\uoa.abdn.ac.uk\global' -D 'CLSM\CGEBM\Bioinformatics Unit\CGEBM Projects Bfx\CGEBMP424A Stefan Marika Targetted RNAseq Nanopore Xenopus tropicalis\Ongoing\' ```
- Note: It doesn't have to be just CLSM\CGEBM etc, it can be any folder in the drive that YOU HAVE ACCESS TO
- Enter your password - this would be your password for your university email
- Once entered, you will now be in the team drive
- Next run the follow commands:
```
recurse on
prompt off
```
- To transfer a folder from the team drive to Maxwell use:
`mget <folder_name_or_path>`
- To transfer a single file from the team drive to Maxwell use:
- Change into the folder holding desired file: `cd <path/to/folder>`
`get myfile.fasta`
- To transfer a folder to the team drive from Maxwell, use:
`mput <folder_in_maxwell>`
- To transfer a single file to the team drive from Maxwell, use:
`put myfile.fasta`
- Once finished, exit smbclient with `exit`
- For more information: https://uoa.freshservice.com/support/solutions/articles/577518

### Setting up slurm environment to use conda
1. ` module load miniconda3` load miniconda3, this is already on Maxwell
2. `conda init bash` make  conda available everytime we connect
3. `source ~/.bashrc` and then we are set

### Moving data between clusters 
1. compress the file `tar -cvzf data.tar.gz data`
2. create md5checksum `md5sum data.tar.gz`
3. copy files from the local computer to the HPC  
`rsync -auvh --progress path/to/source_folder <user>@login.hpc.cam.ac.uk:path/to/target_folder`  
4. copy files from the HPC to a local directory  
`rsync -auvh --progress <user>@login.hpc.cam.ac.uk:path/to/source_folder path/to/target_folder`  
5. check md5 on moved data
6. Decompress file `tar -xvzf data.tar.gz`
