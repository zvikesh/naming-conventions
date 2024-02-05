 The Class CL_ABAP_PARALLEL is provided to support parallel processing of ABAP Code. <br>
 <br>
 The following two examples shows the usage of the class CL_ABAP_PARALLEL. <br>
 <br>
 In the first example the method RUN_INST of class CL_ABAP_PARALLEL is used. The method can be used<br>
 to perform the parallel processing for instances of ABAP Objects. <br>
 <br>
 First you have to define a processing class, which implements the interface <br>
 IF_ABAP_PARALLEL. The parallel processing starts with method IF_ABAP_PARALLEL~DO. <br>
 The method in the example computes the square of a value. <br>
 <br>
 class LCL_PARALLEL_TASK definition. <br>
   public section.  <br>
     interfaces IF_ABAP_PARALLEL. <br>
     methods CONSTRUCTOR importing P_INPUT type I. <br>
     data INPUT  type I. <br>
     data RESULT type I. <br>
 endclass.  <br>
 <br>
 class LCL_PARALLEL_TASK implementation. <br>
 <br>
   method CONSTRUCTOR. <br>
     SUPER->CONSTRUCTOR( ). <br>
     INPUT = P_INPUT. <br>
   endmethod. <br>
<br>
   method IF_ABAP_PARALLEL~DO. <br>
     RESULT = INPUT * INPUT. <br>
   endmethod. <br>
<br>
 endclass. <br>
<br>
 Afterwards the parallel processing has to be started via method RUN_INST. The input for this method is a list of instances of the
 processsing class. The output is also a list of instances of the processsing class plus additional information. <br>
  <br>
 class LCL_TEST_INST implementation.  <br>
   method START.  <br>
     data:  <br>
       L_IN_TAB type CL_ABAP_PARALLEL=>T_IN_INST_TAB,  <br>
       L_INST   type ref to LCL_PARALLEL_TASK.  <br>

     data(L_REF) = new CL_ABAP_PARALLEL( ).  <br>
 <br>
     do 1000 times.  <br>
       append new LCL_PARALLEL_TASK( SY-INDEX ) to L_IN_TAB.  <br>
     enddo.  <br>
 <br>
     L_REF->RUN_INST( exporting P_IN_TAB = L_IN_TAB importing P_OUT_TAB = data(L_OUT_TAB) ).  <br>
  <br>
     loop at L_OUT_TAB assigning field-symbol(&lt;L_OUT&gt;) where INST is not initial.  <br>
       L_INST ?= &lt;L_OUT&gt;-INST.<br>
       " use result in L_INST->RESULT. <br>
     endloop.  <br>
 <br>
   endmethod. <br>
 <br>
 endclass. <br>

 In the second example the method RUN of class CL_ABAP_PARALLEL is used.
 In the example the numbers 1 to 1000000 are multiplied by a constant factor.
 The factor is passed as an attribute of the processing class LCL_PARALLEL.
 The numbers are passed as parameters to the tasks
 <br>
 class LCL_PARALLEL definition final  <br>
     inheriting from  CL_ABAP_PARALLEL.  <br>
   public section.  <br>
     methods DO redefinition.  <br>
     methods CONSTRUCTOR importing P_FACTOR type I.  <br>
     data FACTOR type INT8.  <br>
 endclass.  <br>
 <br>
 class LCL_TEST definition. <br>
   public section.  <br>
     class-methods START. <br>
 endclass.  <br>
 <br>
 LCL_TEST=>START( ). "Start the processing <br>
 <br>
 class LCL_TEST implementation. <br>
   method START.  <br>
     data:  <br>
       L_REF    type ref to LCL_PARALLEL,  <br>
       L_IN_TAB type CL_ABAP_PARALLEL=>T_IN_TAB,  <br>
       L_IN     like line of L_IN_TAB,  <br>
       L_OUT    type INT8.  <br>
 <br>
     L_REF = new LCL_PARALLEL( 100 ).  <br>
 <br>
     do 1000000 times.  <br>
       call transformation ID source IN = SY-INDEX  <br>
                              result xml L_IN.  <br>
       append L_IN to L_IN_TAB.  <br>
     enddo.  <br>
 <br>
     L_REF->RUN( exporting P_IN_TAB = L_IN_TAB importing P_OUT_TAB = data(L_OUT_TAB) ) <br>.
 <br>
     loop at L_OUT_TAB assigning field-symbol(&lt;L_OUT&gt;). <br>
       call transformation ID source xml &lt;L_OUT&gt;-RESULT  <br>
                              result OUT = L_OUT.  <br>
       " use result in L_OUT  <br>
     endloop.  <br>
 <br>
   endmethod. <br>
 <br>
 endclass. <br>
 <br>
  <br>class LCL_PARALLEL implementation.
 <br>
  method CONSTRUCTOR.  <br>
     SUPER->CONSTRUCTOR( ).   <br>
     FACTOR = P_FACTOR.   <br>
   endmethod.   <br>
  <br>
   method DO.  <br>
     data:   <br>
       L_IN  type INT8,   <br>
       L_OUT type INT8.   <br>
  <br>
      call transformation ID source xml P_IN   <br>
                             result IN = L_IN.   <br>
  <br>
      L_OUT = L_IN * FACTOR .  <br>.

      call transformation ID source OUT = L_OUT   <br>
                             result xml P_OUT.   <br>
   endmethod.   <br>
  <br>
 endclass.  <br>
