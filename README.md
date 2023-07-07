# fasrc-ood-jupyter
OnDemand app for serving Jupyter notebooks out of your local path, so you can conveniently manage Jupyter extensions according to your preferences.

**News:** This repository has been updated to ensure compatibility with the [FAS RC Rocky upgrade](https://docs.rc.fas.harvard.edu/kb/rocky-8-transition-guide/) in June 2023.

### Prerequisites
You must have a conda/mamba environment with jupyter lab/notebook installed inside. According to the [FASRC documentation](https://github.com/fasrc/User_Codes/blob/master/Languages/Python/Mamba.md), here is a step by step guide about how to set one:

1. Connect to the RC VPN and log in to the RC cluster via SSH:

   ```shell
   ssh user_name@login.rc.fas.harvard.edu
   ```

2. In your ssh session, Load the Python module, which will automatically load the Mamba module:
   
   ```shell
   module load python/3.10.9-fasrc01
   ```
   Confirm that the modules are loaded by running module list:
   ```shell
   Currently Loaded Modules:
   1) Mambaforge/22.11.1-fasrc01   2) python/3.10.9-fasrc01
   ```

3. Configure your `.condarc` file to install environments in the lab tier 1 storage for better performance:
   
   ```shell
   mkdir /n/hekstra_lab/people/<user_name>/envs
   ```
   Add the following block to your `~/.condarc` file. Create the file if it doesn't exist:
   ```shell
   envs_dirs:
      - /n/hekstra_lab/people/<user_name>/envs
   ```

4. Create a Mamba environment with a custom name:

   ```shell
   mamba create -n <env_name> python=3.10
   ```
   *Note:* For GPU-accelerated deep learning frameworks, refer to the documentation on setting up compatible environments:
   [pytorch](https://github.com/fasrc/User_Codes/tree/master/AI/PyTorch), [tensorflow](https://github.com/fasrc/User_Codes/tree/master/AI/TensorFlow)

5. Activate the newly created environment, install Jupyter Lab (required), and any additional packages you need:

   ```shell
   mamba activate <env_name>
   pip install jupyterlab
   pip/mamba/conda install <other_packages_you_need>
   ```

### Installation
 1) First, you need to [enable the FAS RC VPN](#rc-vpn)
 2) Create a new folder in your home directory on the RC cluster
    `mkdir ~/fasrc/dev`
 3) Navigate to the Open OnDemand app [page](https://rcood.rc.fas.harvard.edu/pun/sys/dashboard)
 4) Click on the `</> Develop` dropdown (top right) and go to "My SandBox Apps (Development)"
 5) Click on "New App" (top left)
 6) Click on "Clone Existing App"
 7) Fill in some suitable directory name. This will determine the name of the directory inside `~/fasrc/dev` used for this project
 8) Paste the following into the "Git remote" dialog box
    ```shell
     https://github.com/Hekstra-Lab/fasrc-ood-jupyter.git
    ```
 9)  Click "Submit"

### Launching
 1) Go to the vdi [interactive session](https://rcood.rc.fas.harvard.edu/pun/sys/dashboard/batch_connect/sessions)
 2) Click on "CustomizedJupyter" (left bottom, Interactive Apps Sandbox section)
 3) Fill out the form and click submit

When the notebook is ready, a "Connect to Jupyter" button will appear. 

### RC VPN
 - General [instructions](https://docs.rc.fas.harvard.edu/kb/vpn-setup/) for the RC VPN are available in the FASRC docs
 - Linux specific instructions using `openconnect` [here](https://docs.rc.fas.harvard.edu/kb/linux-vpn/)

