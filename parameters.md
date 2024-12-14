@AbapCatalog.viewEnhancementCategory: [#NONE]

@AccessControl.authorizationCheck: #NOT_REQUIRED

@EndUserText.label: 'CDS Views with Parameters'

@Metadata.ignorePropagatedAnnotations: true

@ObjectModel.usageType:{

   serviceQuality: #X,

   sizeCategory: #S,

   dataClass: #MIXED

}

define view entity ZPK_SAMPLE02

 with parameters

   p_vbeln : abap.char(10)

  , p_vkorg : abap.char(4)

//    @Environment.systemField : #SYSTEM_DATE

//    p_date  : abap.dats

 as select from I_SalesDocument

   inner join   I_SalesDocumentItem

   on I_SalesDocument.SalesDocument = I_SalesDocumentItem.SalesDocument

{

 key I_SalesDocument.SalesDocument     as SaleDoc,

     I_SalesDocument.SalesOrganization as SalesOrg,

     I_SalesDocumentItem.SalesDocumentItem,

     I_SalesDocumentItem.Material,

     1                                 as num_lit,

     'cds'                             as char_lit,   

//      $parameters.p_date                as syst_date

   I_SalesDocumentItem.BillToParty,

   min(I_SalesDocumentItem._BillToParty.AddressID) as minimum

  

}

where

 I_SalesDocument.SalesDocument = $parameters.p_vbeln

   and I_SalesDocument.SalesOrganization = $parameters.p_vkorg
