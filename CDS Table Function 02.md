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
