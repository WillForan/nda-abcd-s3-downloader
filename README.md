# ABCD HCP BIDS App Derivatives Downloader

This tool can be used to download derivatives from the abcd-hcp-pipeline BIDS App. The derivatives are hosted by the NDA on an aws s3 bucket. 


## Usage

To use this downloader you must first have an NDA account and acquire collection_3165_manifest_s3_links.csv from the [NDA's website](https://ndar.nih.gov/)

You must also provide a list of the derivative types you wish to download. For simplicity a list of all possible derivatives is provided with this repository: basename_derivatives.txt. If you would only like a subset of derivatives it is recommended that you copy only the derivative types that you want into a new .txt file and point to that when calling derivatives_downloader.py

```
usage: derivatives_downloaders [-h] --s3-spreadsheet S3_FILE
                               [--subject-list SUBJECT_LIST_FILE]
                               [--derivatives-file BASENAMES_FILE]
                               [--output OUTPUT] [--credentials CREDENTIALS]

This python script takes in a list of derivatives and a list of
subjects/sessions and downloads the corresponding derivatives using the s3
links

optional arguments:
  -h, --help            show this help message and exit
  --s3-spreadsheet S3_FILE, -x S3_FILE
                        Path to the .csv file downloaded from the NDA
                        containing s3 links for all subjects and their
                        derivatives.
  --subject-list SUBJECT_LIST_FILE, -s SUBJECT_LIST_FILE
                        Path to a .txt file containing a list of subjects for
                        which derivatives and inputs will be downloaded. By
                        default if no
  --derivatives-file BASENAMES_FILE, -d BASENAMES_FILE
                        Path to a .txt file containing a list of all the
                        derivative basenames to downloadfor each subject. By
                        default all the possible derivatives and inputs will
                        be willbe used. This is the derivative_basename.txt
                        file included in this repository. To select a subset
                        it is recomended that you simply copy this file and
                        remove allthe basenames that you do not want.
  --output OUTPUT, -o OUTPUT
                        Path to folder which NDA data will be downloaded into.
                        By default, data will be downloaded into the /home/exa
                        cloud/lustre1/fnl_lab/projects/ABCD/download/derivativ
                        es folder. A folder will be created at the given path
                        if one does not already exist.
  --credentials CREDENTIALS, -c CREDENTIALS
                        Path to config file with NDA credentials. If no config
                        file exists at this path yet, then one will be
                        created. Unless this option or --username and
                        --password is added, the user will be prompted for
                        their NDA username and password. By default, the
                        config file will be located at
                        /home/users/perronea/.abcd2bids/config.ini

``` 
