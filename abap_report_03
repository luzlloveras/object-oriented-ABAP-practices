*&---------------------------------------------------------------------*
*& Report zrep3
*&---------------------------------------------------------------------*
*& This code shows how to use the Widening cast (downcasting)
*& Widening cast can be used when we need to access the Specific
*& functionality of the subclass from the Superclass.
*& It is necessary to catch the exception CX_SY_MOVE_CAST_ERRIR
*& while doing the widening cast to avoid the short-dump.
*&---------------------------------------------------------------------*
REPORT zrep3.

*--------- Animal Super Class definition
CLASS lcl_animal DEFINITION.
    PUBLIC SECTION.
        METHODS: hungry.
ENDCLASS.                   "lcl_animal DEFINITION

*--------- Lion subclass definition
CLASS lcl_lion DEFINITION INHERITING FROM lcl_animal.
    PUBLIC SECTION.
        METHODS: hungry REDEFINITION,
                 fasting.
ENDCLASS.                   "lcl_lion DEFINITION

*--------- Animal Implementation
CLASS lcl_animal IMPLEMENTATION.
    METHOD hungry.
        WRITE: /'An animal is hungry'.
    ENDMETHOD.      "hungry
ENDCLASS.           "lcl_animal IMPLEMENTATION

*--------- Lion subclass Implementation
CLASS lcl_lion IMPLEMENTATION.
    METHOD hungry.
        WRITE: / 'A Lion (King of Jungle) is hungry.',
                 'Run as fast as you can..!'.
    ENDMETHOD.
    METHOD fasting.
        WRITE: / 'Stop running. Lion is on Fasting today.'.
    ENDMETHOD.
ENDCLASS.           "lcl_lion IMPLEMENTATION

START-OF-SELECTION.
    DATA: lo_animal TYPE REF TO lcl_animal,
          lo_lion TYPE REF TO lcl_lion,
          lo_cast_error TYPE REF TO cx_sy_move_cast_error.

*First we have todo no Narrow casting in order to set the
* Animal reference to LION reference.
DATA: lo_tmp_lion TYPE REF TO lcl_lion.
CREATE OBJECT lo_tmp_lion.
lo_animal = lo_tmp_lion.

*Now, we will do the Widening cast to move the reference from the
* Animal to LION (more specific class).
TRY.
    lo_lion ?= lo_animal.
   CATCH cx_sy_move_cast_error INTO lo_cast_error.
    WRITE: / 'Widening cast failed 1'.
ENDTRY.
IF lo_lion IS NOT INITIAL.
    CALL METHOD lo_lion->hungry(  ).
    CALL METHOD lo_lion->fasting(  ).
ENDIF.

* Now, we will try to do the widening cast without setting up
* the proper object reference in the Super reference.
CLEAR: lo_animal, lo_lion, lo_cast_error.
CREATE OBJECT lo_animal.
TRY.
   lo_lion ?= lo_animal.
 CATCH cx_sy_move_cast_error INTO lo_cast_error.
 WRITE: / 'Widening cast failed 2'.
 ENDTRY.
IF lo_lion IS NOT INITIAL.
    CALL METHOD lo_lion->hungry(  ).
    CALL METHOD lo_lion->fasting(  ).
ENDIF.
