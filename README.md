# Installations
Here is a brief guide to installing programmes from the command line. I have created this guide as I often found installation instructions lacking or to simply not exist.  

## Using Conda
Conda is a simple way to install your own programmes, as it will install all necessary dependencies into one environment.  
```
conda create -n enviro_name
conda activate enviro_name
conda install -instructionsfromconda namefromconda
#conda deactivate
```

## Get files
If you can get a link to the repository
```
cd sharedscratch/apps
wget url
```
If there is a GitHub page with a green code button, copy the link from here
```
cd sharedscratch/apps
git clone url
```
If there is no way to get a link, download to laptop the move onto HPC.

### tar.gz file type
Find documentation to check configure/make process. There should be a README file
```
tar xvfz progname.tar.gz #to unpackage
cd progdirectory
./configure #and/or
make
```

#### to use the executable file
```
~/sharedscratch/apps/programme -h
./programme -h
#or add programme directory to file path
```
#### add programme to file path
To use programme from any location  
_See_ https://opensource.com/article/17/6/set-path-linux  
```
PATH=$PATH:~/sharedscratch/apps/programme
programme -h
```
### package without any file extensions
```
chmod u+x programme #make file executable
```

