# From the Documentation

The Class CL_ABAP_PARALLEL is provided to support parallel processing of ABAP Code. 

The following two examples shows the usage of the class CL_ABAP_PARALLEL. 
- In the first example the method RUN_INST of class CL_ABAP_PARALLEL is used. The method can be used to perform the parallel processing for instances of ABAP Objects. 
- First you have to define a processing class, which implements the interface IF_ABAP_PARALLEL. The parallel processing starts with method IF_ABAP_PARALLEL~DO. 

The method in the example computes the square of a value. 

 class LCL_PARALLEL_TASK definition. 
 public section. 
 interfaces IF_ABAP_PARALLEL. 
 methods CONSTRUCTOR importing P_INPUT type I. 
 data INPUT type I. 
 data RESULT type I. 
 endclass. 

 class LCL_PARALLEL_TASK implementation. 

 method CONSTRUCTOR. 
 SUPER->CONSTRUCTOR( ). 
 INPUT = P_INPUT. 
 endmethod. 

 method IF_ABAP_PARALLEL~DO. 
 RESULT = INPUT * INPUT. 
 endmethod. 

 endclass. 

 Afterwards the parallel processing has to be started via method RUN_INST. The input for this method is a list of instances of the processsing class. The output is also a list of instances of the processsing class plus additional information. 

 class LCL_TEST_INST implementation. 
 method START. 
 data: 
 L_IN_TAB type CL_ABAP_PARALLEL=>T_IN_INST_TAB, 
 L_INST type ref to LCL_PARALLEL_TASK. 
 data(L_REF) = new CL_ABAP_PARALLEL( ). 

 do 1000 times. 
 append new LCL_PARALLEL_TASK( SY-INDEX ) to L_IN_TAB. 
 enddo. 

 L_REF->RUN_INST( exporting P_IN_TAB = L_IN_TAB importing P_OUT_TAB = data(L_OUT_TAB) ). 

 loop at L_OUT_TAB assigning field-symbol(<L_OUT>) where INST is not initial. 
 L_INST ?= <L_OUT>-INST.
 " use result in L_INST->RESULT. 
 endloop. 

 endmethod. 

 endclass. 
 In the second example the method RUN of class CL_ABAP_PARALLEL is used. In the example the numbers 1 to 1000000 are multiplied by a constant factor. The factor is passed as an attribute of the processing class LCL_PARALLEL. The numbers are passed as parameters to the tasks 
 class LCL_PARALLEL definition final 
 inheriting from CL_ABAP_PARALLEL. 
 public section. 
 methods DO redefinition. 
 methods CONSTRUCTOR importing P_FACTOR type I. 
 data FACTOR type INT8. 
 endclass. 

 class LCL_TEST definition. 
 public section. 
 class-methods START. 
 endclass. 

 LCL_TEST=>START( ). "Start the processing 

 class LCL_TEST implementation. 
 method START. 
 data: 
 L_REF type ref to LCL_PARALLEL, 
 L_IN_TAB type CL_ABAP_PARALLEL=>T_IN_TAB, 
 L_IN like line of L_IN_TAB, 
 L_OUT type INT8. 

 L_REF = new LCL_PARALLEL( 100 ). 

 do 1000000 times. 
 call transformation ID source IN = SY-INDEX 
 result xml L_IN. 
 append L_IN to L_IN_TAB. 
 enddo. 

 L_REF->RUN( exporting P_IN_TAB = L_IN_TAB importing P_OUT_TAB = data(L_OUT_TAB) ) 
. 
 loop at L_OUT_TAB assigning field-symbol(<L_OUT>). 
 call transformation ID source xml <L_OUT>-RESULT 
 result OUT = L_OUT. 
 " use result in L_OUT 
 endloop. 

 endmethod. 

 endclass. 


class LCL_PARALLEL implementation. 
 method CONSTRUCTOR. 
 SUPER->CONSTRUCTOR( ). 
 FACTOR = P_FACTOR. 
 endmethod. 

 method DO. 
 data: 
 L_IN type INT8, 
 L_OUT type INT8. 

 call transformation ID source xml P_IN 
 result IN = L_IN. 

 L_OUT = L_IN * FACTOR . 
. call transformation ID source OUT = L_OUT 
 result xml P_OUT. 
 endmethod. 

 endclass. 

