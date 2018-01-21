Pull this GitHub repo recursively to get the necessary submodules:
```shell
git clone --recursive https://github.com/krdav/SPURF.git
git pull --recurse-submodules https://github.com/krdav/SPURF.git
```

Dependencies:
conda (installation guide here: https://conda.io/docs/user-guide/install/linux.html)
HMMER (installation guide here: http://hmmer.org/ or use apt-get: sudo apt-get install hmmer)

Use the INSTALL executable to install the required python environment and partis (via `./INSTALL`). Notice that HMMER3 is required in the PATH since this is a dependency of ANARCI (for AHo annotation). Installing partis may require extra attention. We have tested the installation on a fresh Ubuntu installation and running the following will satisfy the extra partis requirements:
```
sudo apt-get install libz-dev cmake scons libgsl0-dev libncurses5-dev libxml2-dev libxslt1-dev mafft
```

With Docker:
cd SPURF
docker build -t spurf .
sudo docker run -it -v /:/host spurf /bin/bash



After installation, the conda environment needs to be loaded every time before use, like this:
```shell
source activate SPURF
```

Then, use the Rscript to infer a substitution profile for your input sequence:
```
Rscript --vanilla run_SPURF.R <input_sequence> <output_base>
E.g.:
Rscript --vanilla run_SPURF.R CGCAGGACTGTTGANGCCTTCGGAGACCCTGTCCCTCACCTGCGTTGTCTCTGGCGGGTCCTTCAGTGATTACTACTGGAGCTGGATCCATCAGCCCCCAGGGAAGGGGCTGGAGTGGATTGGGGAAATCAATCATAGTGGGAGCACCAACTACAACCCGTCCCTCGAAAGTCGAGCCACCATATCAGTAGACACGTCCCAGAACAACCTCTCCCTGAAGCTGAGCTCTGTGACCGCCGCGGACTCGGCTGTGTATTACTGTGCGAGAGGCCCGACTACAATGGCTCACGACTTTGACTACTGGGGCCAGGGAACCCTGGTCACC seqXYZ_SPURF_output
```

The output is a PSSM and a logo plot of this PSSM.


