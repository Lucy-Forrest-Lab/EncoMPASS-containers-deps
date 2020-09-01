# Container for EncoMPASS development

Singularity definition files to install and distribute the dependencies of the
tools used in the development and maintenance of the
[EncoMPASS](https://encompass.ninds.nih.gov/) database.

This repository *does not include the scientific software itself*.

Links to pre-built container images (can be used immediately with Singularity available):
- [Ubuntu 18.04](https://cloud.sylabs.io/library/giacomofiorin/default/encompass-development#container-5edf06ffb1793638c11335b2) with dependencies only (no apps packaged). This is suitable for building and installing the apps on your own, using a writable directory mounted as `/EncoMPASS` in the container (see `--bind` in the Singularity user guide).

Singularity documentation: https://sylabs.io/guides/latest/user-guide/

## List of applications (to be) packaged

Commands should be run inside the container, or passed as an argument to it
(or to an explicit `singularity exec` command). Don't forget to escape the `$`
sign as `\$` (shell variables are defined inside the container).

## AnAnaS 0.9
  Link: https://team.inria.fr/nano-d/software/ananas/  
  Pre-compiled static executable.  
  Test command line:
```
$ ananas $ENCOMPASS_DIR/1okc.pdb
```

## CESymm 2.1.0 and QuatSymm 2.1.0
  Link: https://github.com/rcsb/symmetry/releases/tag/symmetry-2.1.0  
  Java packages, with shell script wrappers; original scripts modified to use 30G of max allocatable memory (backed up as `run_*_small.sh`).  
  Test command line:
```
$ runCESymm.sh -J $ENCOMPASS_DIR/1okc.pdb --stats
```

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
