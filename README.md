Simple Batch Input
==========================

This ABAP program was created for teaching purposes. His explanation are into this video:

<a href="http://www.youtube.com/watch?v=p1RGHq0QgbE&list=UU1m92lTepCpEYDu08QYCSrw&feature=c4-overview" target="_blank">How to create a simple Batch Input</a>




Installation
------------

Copy the coding and paste to your ABAP environment.



FOLLOW CODING BELLOW:

<div class><pre>

SELECTION-SCREEN BEGIN OF BLOCK b1 WITH FRAME TITLE text-001.
PARAMETERS p_cat TYPE c LENGTH 20.
SELECTION-SCREEN END OF BLOCK b1.

DATA wa_bdcdata TYPE bdcdata.
DATA it_bdcdata TYPE TABLE OF bdcdata.
DATA opt TYPE ctu_params.

CLEAR wa_bdcdata.
wa_bdcdata-program  = 'SAPLSD_ENTRY'.
wa_bdcdata-dynpro   = '1000'.
wa_bdcdata-dynbegin = 'X'.
APPEND wa_bdcdata TO it_bdcdata.

CLEAR wa_bdcdata.
wa_bdcdata-fnam  = 'RSRD1-DDTYPE'.
wa_bdcdata-fval   = 'X'.
APPEND wa_bdcdata TO it_bdcdata.

CLEAR wa_bdcdata.
wa_bdcdata-fnam  = 'RSRD1-DDTYPE_VAL'.
wa_bdcdata-fval   = p_cat.
APPEND wa_bdcdata TO it_bdcdata.
*
CLEAR wa_bdcdata.
wa_bdcdata-fnam  = 'BDC_OKCODE'. "SIGINIFICA 'ENTER' OU CLIQUE DE SELEÇÃO
wa_bdcdata-fval   = 'WB_DISPLAY'.
APPEND wa_bdcdata TO it_bdcdata.

opt-dismode = 'E'.



CALL TRANSACTION 'SE11' USING it_bdcdata OPTIONS FROM opt.
</pre></div>
___________
