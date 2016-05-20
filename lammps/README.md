**Instructions**:  
Put "pair_lj_cut_tip4pwwa_long.h" and "pair_lj_cut_tip4pwwa_long.cpp" at the LAMMPS src folder  
Recompile lammps

**The pair style is defined as**:   
pair_style lj/cut/tip4pwwa/long otype htype btype atype qhist ljcut qcut nwtype wtype1 wtype2 … wtypenw

**Syntax**  
otype, htype = atom types for TIP4P O and H  
bytpe, atype = bond and angle types for TIP4P waters  
qdist = distance from O atom to the massless charge M (distance units)  
ljcut = global cutoff for the LJ interaction (distance units)  
qcut = global cutoff for  the Coulombic interaction (distance units)  
nwtype = number of types of atoms that interact with M, not O, in computing the LJ interaction  
wtype1, wtype2, …, wtypenw = types of atoms that interact with M, not O, in computing the LJ interaction

**Example**  
Pair_style lj/cut/tip4pwwa/long 3 4 1 1 0.15 14.0 14.0 2 1 2

**An example input file for using the parameters**  
pair_style    lj/cut/tip4p/long 3 4 1 1 0.15 14.0 14.0 2 1 2  
pair_coeff      1 1  0.0949 3.453       # B-B  
pair_coeff      2 2  0.1448 3.365       # N-N  
pair_coeff      3 3  0.1550 3.154       # O-O  
pair_coeff      4 4  0.0     0.0        # H-H  
pair_coeff      1 2  0.0     0.0        # B-N  
pair_coeff      1 3  0.0981 3.322       # B-O  
pair_coeff      1 4  0.0     0.0        # B-H  
pair_coeff      2 3  0.1213 3.278       # N-O  
pair_coeff      2 4  0.0     0.0        # N-H  
pair_coeff      3 4  0.0     0.0        # O-H  

kspace_style    pppm/tip4p 1e-05  
dielectric      1.0  

bond_style      harmonic  
bond_coeff      1 19.513 0.9572

angle_style     harmonic  
angle_coeff     1 2.385 104.5199

group           fluidmols type 3 4

fix 1 fluidmols shake 0.0001 20 0 b 1 a 1
