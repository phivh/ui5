# UI5 ![alt text](https://sapui5.hana.ondemand.com/resources/sap/ui/documentation/sdk/images/logo_ui5.png "SAPUI5")
[Markdown CheatSheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

>First hint: How to be a god Ui5 developer? Drink 5 glasses of beer everyday.

### Table of Contents
1. **[1way 2way](#1way-2way)**<br>
2. **[Filter/Sort change Server/Client Mode](#filtersort-change-serverclient-mode)**<br>
3. **[Sort NUMC Field](#sort-numc-field)**<br>

## 1way 2way

<pre>
var mParameters = {
   defaultBindingMode : "OneWay" ("TwoWay" depending on requirement)
   defaultOperationMode: "Client" ("Server" depending on requirement)
   defaultCountMode: sap.ui.model.odata.CountMode.None
};
</pre>

## Filter/Sort change Server/Client mode

<pre>
  var oList = this.getView().byId("id_vepdvlistTab");
  var oBinding = oList.getBinding("items");
  if (oBinding.aAllKeys === null) {
   oBinding.sOperationMode = "Client";
   oBinding.aAllKeys = oBinding.aKeys;
  }
  oBinding.aApplicationFilters = aFilters;
  oBinding.filter(aFilters, "Applications");
</pre>

## Sort NUMC Field

<pre>
  oSorter = new sap.ui.model.Sorter("Lifnr", false, false);
   oSorter.fnCompare = function(value1, value2) {
    return oThis.compareIntegers(value1, value2);
   };
   this.getView().byId('id_vendorlist').getBinding('items').sort([oSorter]);


/*Compare integers */
 compareIntegers: function(value1, value2) {
  if ((value1 == null || value1 == undefined || value1 == '') && (value2 == null || value2 == undefined || value2 == '')) {
   return 0;
  }
  if ((value1 == null || value1 == undefined || value1 == '')) {
   return -1;
  }
  if ((value2 == null || value2 == undefined || value2 == '')) {
   return 1;
  }
  if (parseInt(value1) < parseInt(value2)) {
   return -1;
  }
  if (parseInt(value1) == parseInt(value2)) {
   return 0;
  }
  if (parseInt(value1) > parseInt(value2)) {
   return 1;
  }
 }
</pre>
