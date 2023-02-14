# Installations

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
If there is no way to get a link, download to laptop the move onto HPc

### tar.gz file type
Find documentation to check configure/make process. There should be a README file
```
tar xvfz progname.tar.gz #to unpackage
cd progdirectory
./configure #and/or
make
```

### package w/o any file extensions
```
chmod u+x programme #make file executable
```
#### to use the executable file
```
~/sharedscratch/apps/programme -h
./programme -h
#or add programme directory to file path
```
#### add programme to file path
To use programme from any location
```
PATH=$PATH:~/sharedscratch/apps/programme
programme -h
```
## Using Conda
```
conda create -n enviro_name
conda activate enviro_name
conda install -instructionsfromconda namefromconda
#conda deactivate
```
