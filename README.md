# Container for EncoMPASS development and maintenance

Development of the [EncoMPASS](https://encompass.ninds.nih.gov/) database was
carried out using multiple applications, whose dependencies are collected in
a container in Singularity/Apptainer format.

This repository *does not include the scientific software itself*.

The file `Ubuntu1804-EncoMPASS.def` contains the definition file to build
this container.  There is also a
[link](https://cloud.sylabs.io/library/giacomofiorin/default/encompass-development)
to a pre-built container image for the amd64 architecture.

To use the apps below, install them in a local folder writable by you and run
the container while mounting that folder as `/EncoMPASS` (see the option
`--bind` in the Singularity/Apptainer user guide).

Singularity documentation: https://sylabs.io/guides/latest/user-guide/
Apptainer documentation: https://apptainer.org/docs


## List of applications supported by this container

Commands should be run inside the container, or passed as an argument to it
(or to an explicit `singularity exec` command). Don't forget to escape the `$`
sign as `\$` (shell variables are defined inside the container).

## AnAnaS 1.1
  Link: https://team.inria.fr/nano-d/software/ananas/  
  Pre-compiled static executable.  
  Test command line:
```
$ ananas $ENCOMPASS_DIR/1okc.pdb
```

## CESymm 2.2.3 and QuatSymm 2.2.3
  Link: https://github.com/rcsb/symmetry  
  Java packages, with shell script wrappers; original scripts modified to use 30G of max allocatable memory (backed up as `run_*_small.sh`).  
  Test command line:
```
$ runCESymm.sh -J $ENCOMPASS_DIR/1okc.pdb --stats
```
  CESymm 2.1.0 and QuatSymm 2.1.0 are also available in the container.

## DSSP 3.1.5 and HSSP 3.1.5
  Link: https://github.com/cmbi/dssp https://github.com/cmbi/hssp  
  Dynamically linked executable, built in the container.  
  Test command line:  
```
$ mkdssp -i $ENCOMPASS_DIR/1okc.pdb
```

## Fr-TM-Align
  Link: http://cssb.biology.gatech.edu/skolnick/files/FrTMalign/index.html  
  Static executable, built in the container.  
  Test command line:  
```
$ frtmalign $ENCOMPASS_DIR/1okc.pdb <other_pdb>
```

## MUSCLE 3.8.31
  Link: https://www.drive5.com/muscle/downloads.htm  
  Pre-compiled static executable.  
  Test command line:  
```
$ muscle3.8.31_i86linux64 -in <inputfile> -out <outputfile>
```

## MUSCLE 5.1.0
  Link: https://github.com/rcedgar/muscle/releases/download/5.1.0/muscle5.1.linux_intel64
  Pre-compiled static executable.
  Test command line:
```
$ muscle5.1.linux_intel64 -in <inputfile> -out <outputfile>
```

## PPM
  Link: n/a  
  Static executable, built in the container.  
  Test command line:
```
$ immers < test.inp
```

## Symd 1.3w and 1.61
  Link: n/a  
  Pre-compiled static executables.  
  Test command line:
```
$ symd1.61-linux $ENCOMPASS_DIR/1okc.pdb
```
