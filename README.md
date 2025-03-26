# Run TreeQSM in Octave

Some notes on how to run TreeQSM in Octave, I needed to do this as the HPC facility did not have a matlab licence. Hoping this will help people in a similar situation :)

## 0. Install Miniconda (only if your conda is not available or conda base environment cannot install Mamba)
Download the Miniconda installation package

`cd ~`

`wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`

Install Miniconda

`bash Miniconda3-latest-Linux-x86_64.sh -u`

Remove the installation package to clean up

`rm Miniconda3-latest-Linux-x86_64.sh`

Initialise Conda on all available shells

`source ~/miniconda3/bin/activate`

`conda init --all`


## 1. Create an environment and install Octave & prerequisties
### Recommend method: using Mamba (a quicker way)

Install Mamba in the Conda base env if you don't have Mamba before:

`conda install conda-forge::mamba`

In the Conda base env, create a new env named 'octave' using Mamba:

`mamba create -n octave -c conda-forge octave cmake cxx-compiler -y`


### Alternative method: using Conda

In the Conda base env, directly create a new env named 'octave' using Conda:

`conda create -n octave -c conda-forge octave cmake cxx-compiler -y`

## 2. Open Octave and install prerequisites
Activate octave env:

`conda activate octave`

Open octave gui:

`octave`

Install packages within octave gui, using octave commands:

`pkg install -forge io`

`pkg install -forge statistics`

Then load the statistics package

`pkg load statistics`

## 3. Update treeqsm.m to save as binary format
Only need to do it for the first time.

`save([inputs.out, '/', str], 'qsm', '-v7')`

## 4. Run as normal!
