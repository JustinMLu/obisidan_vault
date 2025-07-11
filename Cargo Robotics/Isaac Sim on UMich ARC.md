## (UM-ARC) Quick Reference: Accessing GPU Node 

```bash
# 1. SSH into login node
ssh lujust@gl-login1.arc-ts.umich.edu

# 2. Check your actively running jobs
squeue -u lujust

# 3. Connect to the job
srun --jobid=JOBID_NUMBER --pty bash

#4. Test to ensure you're in the GPU node
nvidia-smi
```

## (UM-ARC) Isaac Sim Installation

```bash
# Create and activate venv
conda create -n rlctrl python=3.8
conda activate rlctrl

# From the pytorch website
pip install torch==2.4.1 torchvision==0.19.1 torchaudio==2.4.1 --index-url https://download.pytorch.org/whl/cu124

# Fucking get the right goonerpy
pip install matplotlib numpy==1.21 tensorboard mujoco==3.2.3 pyyaml

# Download IsaacGym from https://developer.nvidia.com/isaac-gym
cd isaacgym/python && pip install -e .

# Install my version of rsl_rl that comes with the repo
cd arcad_gym/rsl_rl && pip install -e .

# Install arcad_gym
cd arcad_gym && pip install -e .
```


## (UM-ARC) Load a newer GCC Module
This is only if you encounter an error telling you that your GCC version is too old when running a training task.

The UMich ARC resources use gcc 8.5.0, which is way too old. As a result, we're going to have to use a newer version to get our training to work.

```bash
# This is how you see your version
gcc --version

# Check available versions
module avail gcc 

# Load a newer GCC
module load gcc/<SELECTED_VERSION>

# Verify it worked 
gcc --version
```
