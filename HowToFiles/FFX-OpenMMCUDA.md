# FFX-OpenMM CUDA for Laboratory iMacs
This is valid as of 5/31/2017, and may change.

If you want to test CUDA-accelerated FFX-OpenMM on the lab iMacs:

Check your OS version. If you don't have OS X version 10.11 or 10.12 (El Capitan or Sierra), you're going to need to upgrade. For the lab iMacs, use the self-service application to install Apple software updates (should be the first thing on the upper left). As of the time of this email, this will get you to 10.11; IT hasn't yet upgraded their stuff for 10.12 and thus forbids upgrading to Sierra.

There is a possibility this upgrade will cause issues with your path; I suggest making copies of `~/.bash_profile`, `~/.profile`, and `~/.bashrc` (if they exist) in case that happens.

Check your graphics, via the apple button and "About This Mac". If it is *not* an NVIDIA graphics card, you will be unable to use CUDA acceleration, though you might be able to manage OpenCL acceleration of fixed-charge force fields. If no CUDA-capable card is present, FFX will fall back on the reference CPU implementation, which is slow, but works.

Download the appropriate CUDA toolkit. Be sure it's the *toolkit* (about 1 GB); the drivers are insufficient. My best guess is that the drivers are enough to let you run CUDA code, but not compile any CUDA code... and OpenMM relies on being able to compile CUDA kernels on the fly.

Install the CUDA toolkit; you'll have to use the Self Service application to give yourself administrator privileges (log in, go to Utilities).

If you don't already have OpenMM, download and install Anaconda3. When finished with that, run this command: "`conda install -c omnia openmm`".

Modify your Bash profile a bit (`~/.bash_profile`):

Find where it installed CUDA, probably under '`/Developer/NVIDIA/CUDA-8.0`'. I'll refer to this as `$CUDALOCATION`

Add `$CUDALOCATION/bin` to your path, and `$CUDALOCATION/lib` to `DYLD_LIBRARY_PATH`.

The relevant lines from my Bash profile:

`export CUDALOCATION='/Developer/NVIDIA/CUDA-8.0'`
`export PATH="${CUDALOCATION}/bin:$PATH"`
`export DYLD_LIBRARY_PATH="${CUDALOCATION}/lib:$DYLD_LIBRARY_PATH"`

If you don't already have FFX-OpenMM working, you will have to add these to your Bash profile (possibly slightly modified depending on where Anaconda is and where Anaconda put OpenMM):

`export OPENMM_PLUGIN_DIR='/anaconda/pkgs/openmm-7.1.0rc1-py36_0/lib/plugins'`
`export JNA_LIBRARY_PATH='/anaconda/pkgs/openmm-7.1.0rc1-py36_0/lib'`

At this point, you can validate by running `ffxc Energy -Dplatform=OMM someFile.pdb`. Note that the energies may not be exact in certain cases, particularly if you have symmetry not supported by OpenMM or force fields that we can't yet translate into OpenMM. It will take a bit the first time, as it's compiling a bunch of CUDA kernels.

If you installed OpenMM prior to the CUDA toolkit, you may want to run '`conda install -c omnia openmm`' a second time; that will permanently compile the CUDA-OpenMM platform instead of forcing FFX to re-compile the CUDA platform each time it runs.

The GTX 650M chips installed on many of the lab iMacs are no powerhouses, having just 512 MB of VRAM and 5-10% of the computational firepower as a P100 accelerator, but they should be enough to at least ensure the code works.

If you're trying to get CUDA-accelerated FFX-OpenMM working on Linux, the process should be reasonably similar: obtain CUDA, Anaconda, OpenMM, and export the appropriate environment variables. If you're trying to get it working on Windows, that's fantastic and I wish you nothing but the absolute best of luck. Stephen and I have tried to no avail, due to some obscure problem with string processing in JNA.
