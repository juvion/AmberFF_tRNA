# AmberFF_tRNA
**Amber force field parameters (based on ff99) for tRNAs**  

*Updated by Xiaoju Zhang 8/5/2014*  

These force field library files are generated for 14 modified residues that appear in yeast tRNA-Asp, tRNA-Phe, and tRNA-iMet, and they are: m1A, t6A, Ar(p), Cm, m5C, m7G, m22G, Gm, m1G, m2G, yW, m5U, D, Ψ, and three terminal 5’ phosphorylated residues: 5’ phosphate adenosine, 5’ phosphate guanosine, and 5’ phosphate uridine.
 
The charges for the modified residues were derived from the RESP fitting procedure. The parameters were derived from AMBER parm99.dat and gaff.dat. Some parameters that were not found in parm99.dat and gaff.dat were adapted from Tim Meyer and David Case's tRNAPhe force field library file. 

**These parameters are suitable for the usage with the parm99 force field. So modify trna2.0.frcmod to other force fields if it is needed.**
 
####The files are:  

* **.prepi files:**  
5AP.prepi, 5GP.prepi, 5UP.prepi, RIA.prepi. Thoese files are the library files for 5’ phosphate adenosine, 5’ phosphate guanosine, 5’ phosphate uridine and Ar(p), which have a terminal phosphate.   
* **trna2.0.lib:**  
This is the library file for all the non-terminal modified residues.
* **trna2.0.frcmod:**  
This is the file that holds all the derived parameters.   



####How to use:
In this demo, I used Amber10, ff99, tRNA-Asp(PDB:3TRA)   


1. 5AP.prepi, 5GP.prepi, 5UP.prepi, RIA.prepi are separated forcefield for residues with 5’-P at terminal. They need to be read before sourcing the leaprc file.  

2. The phosphate name might give error when load pdb files, it is because of the nonstandard residues using ‘O1P’ and ‘O2P’ following previous literature convention. You may just edit the pdb file accordingly or modify the lib file changing them to ‘OP1’, ‘OP2’ accordingly.

leap.in example, load tRNA-asp (3TRA.db).   
—————————  
> $ tleap  # run tleap  
-I: Adding /home/ju/Programs/amber12/dat/leap/prep to search path.  
-I: Adding /home/ju/Programs/amber12/dat/leap/lib to search path.  
-I: Adding /home/ju/Programs/amber12/dat/leap/parm to search path.  
-I: Adding /home/ju/Programs/amber12/dat/leap/cmd to search path.   

> Welcome to LEaP!  
> (no leaprc in search path)

> \> loadAmberPrep 5UP.prepi #5GP  
> \> source $AMBERHOME/dat/leap/cmd/oldff/leaprc.rna.ff99  
> \> loadoff trna2.0.lib  
> \> loadamberparams trna2.0.frcmod  
> \> a = loadpdb 3TRA_leap.pdb 
...
...  
