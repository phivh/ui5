# UI5 ![alt text](https://sapui5.hana.ondemand.com/resources/sap/ui/documentation/sdk/images/logo_ui5.png "SAPUI5")
[Markdown CheatSheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

>First hint: How to be a god Ui5 developer? Drink 5 glasses of beer everyday.

### Table of Contents
**[1way-2way](#1way-2way)**<br>
**[Filter/Sort-change-server/client-mode](#1way-2way)**<br>

## 1way 2way

<pre>
var mParameters = {
   defaultBindingMode : "OneWay" ("TwoWay" depending on requirement)
   defaultOperationMode: "Client" ("Server" depending on requirement)
   defaultCountMode: sap.ui.model.odata.CountMode.None
};
</pre>

## Filter/Sort change server/client mode

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
