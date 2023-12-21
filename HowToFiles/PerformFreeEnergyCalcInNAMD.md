# Perform Free Energy Calculations in NAMD
Free Energy Simulations  
[Tutorial Information](http://www.ks.uiuc.edu/Training/Tutorials/namd/FEP/tutorial-FEP.pdf)

## Create Dual Topology File in VMD
1. Tools used for this part are found in Extensions > Modeling
2. Load wild-type PDB file using File > New Molecule
   * Browse to find file, press load
   * Change file type if needed (PDB, PSF, etc.)
3. Create PSF file using **automatic PSF Builder** tool (Extensions > Modeling)
   * Select parameter file and press "Load input files"
     * Parameters may be changed if needed
   * Press "I'm feeling Lucky"
   * If you don't specify a location for files, it will be in home directory
4. Create solvated file using **Add solvation box** tool
   * Use .pdb and .psf output from autoPSF
   * Check "Use Molecule Dimensions"
   * Make sure "Waterbox Only" is Unchecked
   * Add 10 to "Box Padding" (both min and max)
   * Press Solvate
5. Create dual topology map using **Mutate Reside** tool
   * Use .pdb and .psf output from Solvate tool
   * Usually, you can ignore Segment name
     * Creating dual topology for a structure with more than one chain requires making an autoPSF for each individual chain (will do automatically), creating dual topology map for affected chain *before* solvating, stringing pdb's back together, and then solvating structure last
   * Fill in variant residue number in "ID of target residue"
   * Fill in three letter amino acid abbrv. in "Mutation"
   * Check "Generate FEP" box
   * Add "FEP Prefix" for output files
   * Press "Run Mutator"
6. Make a copy of .fep file output from Mutation tool and name it with .pdb extension at the end of it.
7. Open the fep.pdb file of protein and change all numbers in 2<sup>nd</sup>-to-last column to 0, and all numbers in 3<sup>rd</sup>-to-last to 1's at the residue of interest

## Set parameters of NAMD configuration files
1. You will need:
   * Equilibriate.namd
   * Forward.namd
   * Backward.namd
   * Fep.tcl
   * Parameter file (depending on which 'top' file used in autoPSF)
   * Job file
   * .pdb
   * .psf
   * .fep
2. Input files
3. Output files
4. Coordinates
   * Find coordinates for cell basis vector at top of solvate.pdb
   * Cell origin
     * Open VMD: File > New Molecule
       1. Load .psf and .fep
       2. Select fep as a PDB type file
       3. Open TK Console
          1. Extension > TK Console
          2. Type these commands:
            * `set origin [atomselect top all]`
            * `measure center $origin`
          3. Copy and paste cell origin into configuration files
5. Time-steps
   * Individual time steps are measure by fempto-seconds
6. DCD frequency option
   * Under output frequencies you can opt to add
     * "dcdfreq###" (enter desired number)
7. Lambdas?
   * Found at very bottom of the page (first two numbers)
8. Other?
   * Up to your discretion!

## Analyzing Results
1. Use **FEP simulation analysis** tool with forward and backward .fepout files
   * Select "Bar Estimator" tool
2. Analyze output from simulation analysis tool using Excel
   * Import data as a text file
