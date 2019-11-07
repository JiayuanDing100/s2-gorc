# Semantic Scholar GORC

**Latest release: 2019-09-28**

The Semantic Scholar Graph of References in Context (GORC) dataset is a literature graph of 81.0M academic publications and 380.5M citation edges. 
Full text and citation contexts are available for 8.1M papers. Abstracts are available for 73.4M papers.

The dataset can be downloaded from the S3 bucket `s3://ai2-s2-gorc-release/`. 
The manifest file `s3://ai2-s2-gorc-release/20190928/manifest.json` lists all available files available for download.
The full corpus consists of 10000 files, and is around 870GB uncompressed and 200G compressed.

Example code located in `examples/` uses the boto3 library to access AWS S3, more documentation [here](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/s3-examples.html).

## Download instructions

1. If you have AWS access, skip to the next step. Otherwise, follow the instructions here to create an access key and setup your environment:

    [AWS CreateAccessKey Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey)

2. If you are using AWS CLI

* To download the manifest file:

    `aws s3 cp s3://ai2-s2-gorc-release/20190928/manifest.json gorc/`

* To download all GORC data files:

    `aws s3 cp --recursive s3://ai2-s2-gorc-release/20190928/papers/ gorc/`

3. If you are using Python:

* Setup an environment (below example uses Miniconda)
    * Download the Miniconda installer for your OS: [https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html)
    * Run `bash Miniconda-3.5.5-MacOSX-x86_64.sh` to install
    * Add conda path to $PATH variable
    * Create a conda environment: `conda create -n gorc -y python==3.7`
    * Activate environment: `conda activate gorc`
    * Install requirements: `pip install -r requirements.txt`
    * Install scispacy: `pip install https://s3-us-west-2.amazonaws.com/ai2-s2-scispacy/releases/v0.2.4/en_core_sci_sm-0.2.4.tar.gz`
    
* Download GORC using the script `examples/download_gorc.py`