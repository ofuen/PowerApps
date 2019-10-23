<p align="center">
<img src="https://user-images.githubusercontent.com/19554935/66256981-bc639e80-e761-11e9-8f6c-03e461718035.png"/>
  </p>
  
  
***
<b>Formulas and Rules related to PowerApps</b>
***
##
<b><u>Toggle</u></b>
```Excel
If(Toggle1.Value=true, true, false)
```
##
<b><u>Yes/No</u></b>
```Excel
If(DataCardValue*.Value=true, true, false)
```
##
***
##
<b><u>If Toggle value is NO, N/A will be fill</u></b>
```Excel
If(!(DataCardValue20),"N/A",Parent.Default)
```
##
<b><u>Default Property → Fill in N/A for Required field</u></b>
```Excel
f(!(DataCardValue37),"N/A",Parent.Default)
```
