# Plugins in ug4
Each plugin is composed of two folders: the source code in c++, which has to be cloned to the /plugins/ folder in ug4; and the 
applications with the LUA code, which must ideally be placed in the /apps/ folder.  

The source and LUA files for three optimization strategies are provided:

1. Nonlinear extension equation
2. $p$-Laplacian relaxation
3. Alternate direction method of multipliers

The implementations are self-contained, i.e. indepedent of each other and of other ug4 plugins. 

## Plugin installtion
The corresponding folders for each implementation are:

1. Nonlinear extension equation: NNLOptim/ and obstacle_optim/ 
2. $p$-Laplace: PLaplaceOptim/ and plaplace_optim/
3. ADMM: ADMMOptim/ and admm_optim/

The *_optim folders contain the LUA files, which can be run using the ugshell -ex /path/to/lua/file command.
The *Optim* folders contain the c++ source code which have to be added to the ug4 installation via the *-DPLUGIN_NAME=ON* command. 
The plugins will appear in the list of plugins with the *cmake ..* command. 

# Configuration of ug4 and LUA scripts
UG4 can be installed as indicated in the documentation. The only, non-mandatory, dependencies are the plugins 
corresponding to the SuperLU solver and ParMETIS. If these are not provided, the LUA files have to be modified
accordingly. 

It is worth mentioning some configurations proper of our implementations.
First and foremost, the codes work for dimensions of 2 or 3, so setting up ug4 with *-DDIM=1* leads to failure of the LUA scripts.
To obtain the profiling results, the *Shiny* profiler was used in all cases (*-DPROFILING=Shiny*). 
For usage in a parallel computer, the paths have to be modified to the file system of the user. 


