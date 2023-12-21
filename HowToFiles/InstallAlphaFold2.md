# How To Install AlphaFold2
Create Conda environment:  
`conda create --name alphafold python==3.8`

Update your conda install; this command took 3 days for me:  
`conda update -n base conda`

Activate your environment:  
`conda activate alphafold`

Install each conda package independently:  
`conda install -y -c conda-forge openmm==7.5.1`  
`conda install -y -c conda-forge cudnn==8.2.1.32`  
`conda install -y -c conda-forge cudatoolkit==11.0.3`  
`conda install -y -c conda-forge pdbfixer==1.7`  
`conda install -y -c bioconda hmmer==3.3.2`  
`conda install -y -c bioconda hhsuite==3.3.0`  
`conda install -y -c bioconda kalign2==2.04`

Clone DeepMind's repository:  
`git clone https://github.com/deepmind/alphafold.git`

Set alphafold_path to your git repo location:  
`alphafold_path="/path/to/alphafold/git/repo"`

Get chemical properties:  
`wget -q -P $alphafold_path/alphafold/common/ https://git.scicore.unibas.ch/schwede/openstructure/-/raw/7102c63615b64735c4941278d92b554ec94415f8/modules/mol/alg/src/stereo_chemical_props.txt`

Install each pip package independently:  
`pip install absl-py==0.13.0`  
`pip install biopython==1.79`  
`pip install chex==0.0.7`  
`pip install dm-haiku==0.0.4`  
`pip install dm-tree==0.1.6`  
`pip install immutabledict==2.0.0`  
`pip install jax==0.2.14`  
`pip install ml-collections==0.1.0`  
`pip install numpy==1.19.5`  
`pip install scipy==1.7.0`  
`pip install tensorflow==2.5.0`  
`pip install pandas==1.3.4`  
`pip install tensorflow-cpu==2.5.0`  
`pip install --upgrade jax jaxlib==0.1.69+cuda111 -f https://storage.googleapis.com/jax-releases/jax_releases.html`

Change this cd command to go to your anaconda3 installation:  
`cd ~/anaconda3/envs/alphafold/lib/python3.8/site-packages/ && patch -p0 < $alphafold_path/docker/openmm.patch`

Download a fresh copy of all genetic databases used by AlphaFold from DeepMind; the download_db.sh can be helpful for automating the process:  
https://github.com/deepmind/alphafold#genetic-databases  
[download_db.sh]()

Place the run_alphafold.sh script in the main AlphaFold directory:  
[run_alphafold.sh]()

Example Job Script:  
#$ -r n                      # Restartable  
#$ -ckpt user                # Restart under user; do not change (do not replace with your username)  
#$ -V                        # Inherit current environment  
#$ -cwd                      # Start job in submission directory  
#$ -N COCH                   # Job Name  
#$ -j y                      # Combine stderr and stdout  
#$ -q MS                     # Queue  
#$ -pe 56cpn 56              # Node  
#S -l gpu=true               # GPU  
#$ -o $JOB_NAME.$JOB_ID.log  # Name of output file  
#$ -l h_rt=196:00:00         # Run Time  
#$ -S /bin/bash              # Shell to use  

#ACTIVATE YOUR PREFERRED CONDA ENVIRONMENT  
<code>
source activate alphafold
export NVIDIA_VISIBLE_DEVICES='all'
export TF_FORCE_UNIFIED_MEMORY=1.0
export XLA_PYTHON_CLIENT_MEM_FRACTION=4.0
export OPENMM_CPU_THREADS=8
</code>

#CHANGE LOCATION OF ALHPAFOLD_PATH TO DESIRED PATH

`alphafold_path="/Dedicated/schnieders/programs/alphafold2-github"`

`bash /Dedicated/schnieders/programs/alphafold2-github/run_alphafold.sh -d /Dedicated/schnieders/programs/alphafold2-data/alphafold-data -o . -m monomer -f ./test.fasta -t 2020-05-14`
