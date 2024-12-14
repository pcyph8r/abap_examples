@EndUserText.label: 'CDS table function demonstrating fields type difference'

define table function ZPK_CDSTF02

 with parameters

   @Environment.systemField: #CLIENT

   client : abap.clnt,

   idnum  : abap.char(10)

returns

{

 client   : abap.clnt;

 id       : abap.char(10);

 name     : abap.char(50);

 age      : abap.int4;

 salary   : abap.curr(15,2);

 currency : abap.cuky;

}

implemented by method

 zcl_cdstf02=>get_emp_details;



 CLASS zcl_cdstf02 DEFINITION

 PUBLIC

 FINAL

 CREATE PUBLIC .

 PUBLIC SECTION.

   INTERFACES if_amdp_marker_hdb.

   CLASS-METHODS get_emp_details

       FOR TABLE FUNCTION zpk_cdstf02.

 PROTECTED SECTION.

 PRIVATE SECTION.

ENDCLASS.

CLASS zcl_cdstf02 IMPLEMENTATION.

 METHOD get_emp_details BY DATABASE FUNCTION FOR HDB LANGUAGE SQLSCRIPT

   USING zpk_emp

         zpk_empsal.

   it_result = select zpk_emp.client,

                      zpk_emp.id,

                      name,

                      age,

                      salary,

                      currency

                      from zpk_emp

                      inner join zpk_empsal

                      on zpk_emp.client = zpk_empsal.client

                       and zpk_emp.id = zpk_empsal.id;

   return :it_result;

 endmethod.

ENDCLASS.



*&---------------------------------------------------------------------*

*& Report zpk_cdstf02

*&---------------------------------------------------------------------*

*&

*&---------------------------------------------------------------------*

REPORT zpk_cdstf02.

CLASS demo DEFINITION.

 PUBLIC SECTION.

   CLASS-METHODS main.

ENDCLASS.

CLASS demo IMPLEMENTATION.

 METHOD main.

* Method 1 : to get for utilising the db features class.

*  data(lv_support) = cl_abap_dbfeatures=>use_features(

*    EXPORTING

**      connection         =

*      requested_features = VALUE #( ( cl_abap_dbfeatures=>amdp_table_function ) )

**    RECEIVING

**      supports_features  = data(lv_support)

*).

**  CATCH cx_abap_invalid_param_value.

*    if  lv_support = 'X'.

*

*    endif.

* Method 2 : in if statement directly

   IF ( cl_abap_dbfeatures=>use_features(

           EXPORTING

          requested_features = VALUE #( ( cl_abap_dbfeatures=>amdp_table_function ) )

        )  ).

     SELECT * FROM zpk_cdstf02

     '100' and idnum '01'

     INTO TABLE @DATA(it_result).

     IF sy-subrc IS INITIAL.

       data(lv_counter) = lines( it_result ).

       cl_demo_output=>Write( lv_counter ).

       cl_demo_output=>display( it_result ).

     ENDIF.

   ELSE.

   ENDIF.

 ENDMETHOD.

ENDCLASS.

START-OF-SELECTION.

 demo=>main(  ).
