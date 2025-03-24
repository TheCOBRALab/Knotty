## Install build tools
- Download conda and run `conda install anaconda-client conda-build` to install the build tools and upload tools

## How to build the package locally
- Start in the Knotty folder
- Run `conda build ./conda_recipe` to build package
- Run `conda install --use-local knotty` to install (case sensitive)
- Run `knotty --help` to insure it installed properly (case sensitive)


## Automated Package Build and Upload

### How to build & upload
- Update the version number in meta.yaml
- Draft a new release on github

### Update key (Expires on: 2026/03/19)
- Have an account at https://anaconda.org/ with access to COBRALab
- Got to https://anaconda.org/COBRALab/settings/access
- Check the boxes next to `Allow write access to the API site` & `Allow access to all package repositories`
- Press `Create` and scroll down until you see the name of the key you just created, then press `view`
- Copy the token, and open github, then go to the repository you're trying to update
- Go to settings -> Secrets and variables -> Actions -> Secrets
- Press edit (the little pencil) next to `ANACONDA_API_TOKEN` and paste the new token
- Press `Update secret` and you're done!

## Manual Package Upload
### Setup Conda account (For uploading packages)
- Create an account at https://anaconda.org/
- Type `anaconda login` in terminal and login to your account
- Run `conda config --set anaconda_upload no` to prevent automatic uploads to anaconda after every build

### Upload package
- Find the package you built using `conda build ./conda_recipe --output`
- Type `anaconda upload -u COBRALab /path/to/package.conda`
- You must be added to the organization for this to work
- Please update the version in the meta.yaml file before uploading