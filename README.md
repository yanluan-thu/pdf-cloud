# pdf-cloud
the code of the pdf cloud scheme


 
seven files for macrophysics scheme:
 (eddy_diff.F90; vertical_diffusion.F90; uwshcu.F90; convect_shallow.F90;
 macrop_driver.F90; cldwat2m_macro.F90; cldfrac_conden.F90)

 %%%% 1. add variables into buffer
 vertical_diffusion.F90: call pbuf_add_field(lengi/shi/smi,....)
 |
 eddy_diff.F90: subroutine compute_eddy_diff (..., lengi, shi, smi)

 %%%% 2. add variables into buffer
 convect_shallow.F90: call pubf_add_field(qtu/thlu/explwi2qtu, ...)
 |
 uwshcu.F90: subroutine compute_uwshcu_inv(..., qtu_inv, thlu_inv, explwi2qtu_inv)

 %%%% 3. new cloud scheme works
 macrop_driver.F90 (main program): call mmacro_pcond (); get varibles from buffer:
 (lengi,shi,smi,qtu,thlu,explwi2qtu,…)
 |
 cldwat2m_macro.F90: call all subroutines in cldfrac_conden.F90
 |
 cldfrac_conden.F90: subroutine cldfrac_conden_init
 (),subgrid_var(),cldfrac_conden(),cldfrac_conden_single(),cldfrac_conden_single_only()
