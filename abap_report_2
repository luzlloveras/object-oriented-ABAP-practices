*&---------------------------------------------------------------------*
*& Report zrep2
*&---------------------------------------------------------------------*
*&
*&---------------------------------------------------------------------*
REPORT zrep2.

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

*----- This code shows how to use the Narrow casting
START-OF-SELECTION.
    DATA: lo_animal TYPE REF TO lcl_animal,
          lo_lion TYPE REF TO lcl_lion.

*ANIMAL object without NARROW casting
WRITE: / 'Animal - without NARROW casting'.
CREATE OBJECT lo_animal.
CALL METHOD lo_animal->hungry( ).
CLEAR lo_animal.

*ANIMAL object with NARROW casting
SKIP 2.
WRITE: / 'Animal - NARROW casting from LION'.
CREATE OBJECT lo_lion.
lo_animal = lo_lion.
CALL METHOD lo_animal->hungry( ).

*call the method FASTING must be a dynamic because FASTING is not in the Animal
CALL METHOD lo_animal->('FASTING').
