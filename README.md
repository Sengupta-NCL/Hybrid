# Hybrid
Hybrid simulations of CG and AA


You can refer to these commands while replicating the setup process.

gmx grompp -p *.top -c *.gro -f em-sc.mdp -o em-sc.tpr -maxwarn 2

gmx mdrun -deffnm em-sc -v

gmx grompp -p hybrid.top -c em-sc.gro -f sd-sc.mdp -o sd-sc.tpr -maxwarn 2

gmx mdrun -deffnm sd-sc -v

gmx grompp -p hybrid.top -n run.ndx -c sd-sc.gro -f min.mdp -maxwarn 3

gmx mdrun -v -c min.gro

gmx grompp -p hybrid.top -n run.ndx -c min.gro -r min.gro -f sd1.mdp -maxwarn 3

gmx mdrun -v -c sd1.gro

gmx grompp -p hybrid.top -n run.ndx -c sd1.gro -f sd2.mdp -maxwarn 3

gmx mdrun -v -c sd2.gro

gmx grompp -p hybrid.top -n run.ndx -c sd2.gro -f md1.mdp -maxwarn 3

gmx mdrun -v -c md1.gro
