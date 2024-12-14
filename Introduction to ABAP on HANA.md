# Introduction to ABAP on HANA

As we all know SAP hass a 3 tier architecture.
- Application layer
- Presentation layer
- Database Layer

In ABAP, we used db as Oracle, db6 and others but in ABAP on HANA, SAP came up with there own db. 

In this db, it is pwerful than other legacy db's. Some need to change programming as well. 

Previously, with the old dbs and ABAP , we were doing things on APplication layer. With ABAP on HNA and new db m complex part and process can be handled at db level itself and should be perform there. 

## Why SAP came up with new db ? 
Due to various hardware and software innovations. 
As more efficent hardware are now availble at lower price,, and softwares are also evolving with time more computational power can be achieved. 

## HANA Magic Words :  
- Hardware Innovations
  - In Memory Database 
- Software Innovations
   - Column Store & Row Store
   - Data Compression
   - OLTP vs OLAP
   - Table Partioning
   - Insert Only Approach
   - Code Push Down 
  

## This'll be a _Helpful_ Section About the Greek Letter Θ!
A heading containing characters not allowed in fragments, UTF-8 characters, two consecutive spaces between the first and second words, and formatting.

## Hardware Innovations 
#### In Memory Database
* **Multicore Architecture** -
  Cores helps in handling tasks parallely by breaking tasks into sub tasks and parts and asssigning to each core.
* **Address Space** -
  1 bit stores 2 numbers. 2 bit stores 4 numbers.
  Bits stores 2^n. 32 bit can handle upto 4 GB of memory. If memory is greater than 4 GBm 32 bit cannot handle. so higher memry ram is requried.

  _Price is decreasing and we are getting more performance._


## Software Innovations 
#### Column Store & Row Store

  In HANA db,, SAP started using column store along with row store. 
  
  | Row Store | Column Store |
  |-----|---------------|
  |     Data is stored in db row by row. | Data is stored in db column by column. |


* **Column Store** -

* **Address Space** -
  1 bit stores 2 numbers. 2 bit stores 4 numbers.
  Bits stores 2^n. 32 bit can handle upto 4 GB of memory. If memory is greater than 4 GBm 32 bit cannot handle. so higher memry ram is requried.

  _Price is decreasing and we are getting more performance._





