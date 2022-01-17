# fasrc-ood-jupyter
OnDemand app for serving Jupyter notebooks out of your local path 

### Prerequisites
You must have Jupyter installed and in your path. Most users will want to do this through Anaconda. Anaconda can, owing to filesystem latency, take a very
long time to load on the FASRC cluster. A nice workaround is to ensure that Jupyter is only loaded from the compute nodes. One easy way to do this is
to look at the hostname and only activate conda if it does not contain the string `login`. This can be accomplished by putting the following in your `.bashrc`

```shell
# Only load these modules on the compute nodes
JLAB_ENV=jlab
if [[ $(hostname) != *login* ]]; then
    conda activate $JLAB_ENV
fi
```

### Installation
 1) First, you need to [enable the FAS RC VPN](#rc-vpn)
 2) Create a new folder in your home directory on the RC cluster
    `mkdir ~/fasrc/dev`
 3) Navigate to the Open OnDemand app [page](https://vdi.rc.fas.harvard.edu)
 4) Click on the `</> Develop` dropdown (top right) and go to "My SandBox Apps (Development)"
 5) Click on "New App" (top left)
 6) Click on "Clone Existing App"
 7) Fill in some suitable directory name. This will determine the name of the directory inside `~/fasrc/dev` used for this project
 8) Paste one of the following into the "Git remote" dialog box
    - `https://github.com/Hekstra-Lab/fasrc-ood-jupyter` if you do not have `ssh` configured or do not want to use it
    - `git@github.com:Hekstra-Lab/fasrc-ood-jupyter.git` if you want to sue `ssh`. This requires having an `ssh` key configured on the cluster and registered with your github account.
 9) Click "Submit"

### Launching
 1) Go to the vdi [homepage](https://vdi.rc.fas.harvard.edu)
 2) Click on the Deveop dropdown and go to "My Sanbox Apps (Development)"
 3) Click on "Launch Jupyter Notebook - Local install only"
 4) Fill out the form and click submit

When the notebook is ready, a "Connect to Jupyter" button will appear. 

### RC VPN
 - General [instructions](https://docs.rc.fas.harvard.edu/kb/vpn-setup/) for the RC VPN are available in the FASRC docs
 - Linux specific instructions using `openconnect` [here](https://docs.rc.fas.harvard.edu/kb/linux-vpn/)

