---
title: "11 - /barcode"
menu:
  main:
    name: "/barcode"
    identifier: "sysadmin/eas/api/barcode"
    parent: "sysadmin/eas/api"
---
#  EAS-API: /barcode

##  Example

```url
http://eas.example.com/eas/barcode?value=Gute%20Nacht&target_code=Code128&target_size=512x384&target_quietzones=1&instance=example
```


##  Parameter


|key|value|
|---|---|
|`instance`          |Name of the Instance|
|`value`             |Value of the Barcode, must be compatible with the selected barcode.|
|`target_code`       |Version of the Barcode, Given is `Code128`. Supports `Code128`, `EAN13`, `EAN8`.|
|`target_size`       |Size of the Barcode. Default will choose the smalled possible size. Example: `400x300`|
|`target_quietzones` |When selected (Value `1`) there will be a blank space left and right of the Barcode in the picture. Currently only avaliable for `Code128`.|

 
