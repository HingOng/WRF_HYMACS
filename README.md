WRF_HYMACS is a tool for WRFV3.7.1 which makes it able to implement HYMACS (HYbrid MAss flux Cumulus Schemes)
The modified codes are included in three directories as follows:
WRF_HYMACS/Registry/: Registry.EM_COMMON
WRF_HYMACS/phys/: Makefile, module_cu_hymakf.F, module_cu_mshymakf.F, module_cumulus_driver.F, module_physics_addtendc.F, and module_physics_init.F
WRF_HYMACS/dyn_em/: module_big_step_utilities_em.F, module_em.F, module_first_rk_step_part1.F, module_first_rk_step_part2.F, module_small_step_em.F, solve_em.F, and start_em.F

A. Getting Started:

1. Get source codes:
   Download WRFV3.7.1.TAR.gz

2. Unpack the codes:
     gunzip WRFV3.7.1.TAR.gz
     tar -xf WRFV3.7.1.TAR
   this will create the directory: WRFV3/

3. Copy the modified codes:
     cp WRF_HYMACS/Registry/* WRFV3/Registry/
     cp WRF_HYMACS/phys/* WRFV3/phys/
     cp WRF_HYMACS/dyn_em/* WRFV3/dyn_em/

4. Configure:
   Move to WRFV3/
     ./configure
   you will have to select a platform of computer and a type of nesting run.

5. Compile WRF:
     ./compile wrf >& compile.log &
   this will take about 20 minutes.

6. Compile for idealized tropical cyclone cases
     ./compile em_tropical_cyclone
   About the other cases, see "C. For more information"

7. Run
   (1) Move to run/ or test/em_tropical_cyclone
   (2) If there is a run_me_first.csh script, run it.
   (3) Edit namelist.input
       cu_physics                          =  1, (KF scheme)
                                             11, (multi-scale KF scheme)
                                             12, (HYMACS scheme modified from KF scheme)
                                             13, (HYMACS scheme modified from multiscale KF scheme)
       About the others settings, see "C. for more information"
   (4) Run ideal.exe
   (5) Run wrf.exe (Please ask the manager how to submit a job)

*  3. and 7. (3) are two steps which makes the WRFV3 different from the original version. 

B. To do:
   The HYMACSs are to be tested in cases other than idealized tropical cyclone,
   and the parameters in the schemes are to be tuned.
   These are the code of the HYMACS:
   phys/module_cu_hymakf.F   (modified from phys/module_cu_kfeta.F)
   phys/module_cu_mshymakf.F (modified from phys/module_cu_mskf.F)

C. For more infromation
   WRF ARW Online Tutorial
   http://www2.mmm.ucar.edu/wrf/OnLineTutorial/index.htm
   
****************************************************************
Hing Ong
hwang2@albany.edu
****************************************************************
