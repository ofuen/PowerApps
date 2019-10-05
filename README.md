<p align="center">
<img src="https://user-images.githubusercontent.com/19554935/66256981-bc639e80-e761-11e9-8f6c-03e461718035.png"/>
  </p>
  
  
***
<b>Formulas and Rules related to PowerApps</b>
***
<b>Toggle</b>
```css
If(Toggle1.Value=true, true, false)
```
<b>Yes/No</b>
```css
If(DataCardValue*.Value=true, true, false)
```
***
<b>If Toggle value is NO, N/A will be fill</b>
```css
If(!(DataCardValue20),"N/A",Parent.Default)
```
