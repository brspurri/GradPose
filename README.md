# GradPose

Welcome to the GitHub repository for the GradPose tool.

GradPose is a novel structural superimposition command-line tool and Python package for PDB files. GradPose uses gradient descent to incrementally approach the optimal rotation matrices (via quaternions) for alignment.  It is memory efficient and enables for the quick alignment of thousands to millions of protein structures to a template structure while also providing exact control over which chain and specific residues to align. The tool is designed to overcome the limitations of classical superimposition algorithms, which are not equipped to handle the large number of PDB files produced by researchers today. Our method scales linearly with the number of residues and can also use batch matrix operations effectively even when there are amino-acid insertions or deletions. This makes it more efficient than traditional methods, which tend to scale exponentially with the number of residues and process the pbds individually. Furthermore, if a GPU is available, it can use CUDA acceleration.

This repository contains the source code and documentation for the GradPose tool. Please refer to the documentation for instructions on how to use the tool and for more information about its features and capabilities.

We hope that this tool will be useful to researchers and practitioners in the field of bioinformatics. If you have any questions or suggestions, please don't hesitate to open an issue or submit a pull request. We welcome contributions and feedback from the community.

## Install

Install GradPose from PyPI with pip:
    
```
pip install gradpose
```


## Examples of usage:

A folder containing N PDBs named 'example_pdb_folder'

```
gradpose -i example_pdb_folder
```
or
```
gradpose example_pdb_folder
```
The aligned proteins are automatically stored in the folder 'output'. Using another folder name, or overwriting the current folder without creating a second is possible using the -o option. 


If the pdbs need to be aligned to a specific template:
```
gradpose -i example_pdb_folder -t template_example.pdb
```

If only a spedific part of the proten needs to be aligned, for exmaple, the first 10 amino-acids, animo-acids 12, and the the aminoacids ranging between (and including) 20 and 30:

```
gradpose -i example_pdb_folder -r 1:10 12 20:30
```

(Instructions for options coming soon.)