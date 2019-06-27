Test Google Drive backend for 1000 Genomes Project data 27 June 2019.

To download data from Google Drive:

Initial setup:

1. If you do not have pip3 installed:

```
    sudo apt install python3-pip
```

2. Install the git annex remote for Google Drive:

```
    pip3 install git-annex-remote-googledrive
```

Downloading datasets:

3. download the CONP dataset from your fork of the repository:

```
    datalad install -r http://github.com/<your_user_name>/conp-dataset
```

4. For each project you are interested in: (e.g. conp-dataset/projects/<your_project>):

    - In the project's directory, set up and connect the Google Drive remote:
 
```
    git annex init
    git-annex-remote-googledrive setup
    datalad siblings -d "</full/path/to/your_project>" enable -s google
```

5. Retrieve the files of interest as with other backends

```
    datalad get <your_file_name>
```

Example:

```
  datalad install -r http://github.com/emmetaobrien/conp-dataset
  cd conp-dataset/projects/1KGP-GoogleDrive-27Jun2019
  git annex init
  git-annex-remote-googledrive setup
  datalad siblings -d "/home/emmetaobrien/conp-dataset/projects/1KGP-GoogleDrive-27Jun2019" enable -s google
  datalad get *
```


Notes:

* Only the version of git-annex-remote-googledrive installed with pip3 is observed to work for this process; using older versions of pip can cause problems.

* If the Google Drive remote is not correctly set up, the project directory will appear to contain correctly formed links, but they will not connect to anything.








