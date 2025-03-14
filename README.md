# Run TreeQSM in Octave

Some notes on how to run TreeQSM in Octave, I needed to do this as the HPC facility did not have a matlab licence. Hoping this will help people in a similar situation :)

## 1. Create an environment and install Octave & prerequisties
### Recommend method: using mamba (a quicker way)

Install mamba in the base env if you don't have mamba before:

`conda install conda-forge::mamba`

Create octave env using mamba:

`mamba create -n octave -c conda-forge octave cmake cxx-compiler -y`


### Alternative method: using conda
`conda create -n octave -c conda-forge octave cmake cxx-compiler -y`

## 2. Open Octave and install prerequisites
Activate octave env:

`conda activate octave`

Open octave:

`octave`

Install packages using octave commands:

`pkg install -forge io`

`pkg install -forge statistics`

Then load the statistics package

`pkg load statistics`

## 3. Update treeqsm.m to save as binary format
Only need to do it for the first time.

`save([inputs.out, '/', str], 'qsm', '-v7')`

## 4. Run as normal!
