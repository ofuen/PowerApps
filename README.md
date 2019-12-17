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
***
<b><u>Default Property → Fill in N/A for Required field</u></b>
```Excel
If(!(DataCardValue37),"N/A",Parent.Default)
```
###
***
<b><u>How to make two combo box search to display the content and vice versa</u></b>
```Excel
If(!IsBlank(cbAddress.Selected.Text), 
Filter(dataSource, addressColumn = cbAddress.Selected.Text), 
!IsBlank(cbJobNumber.Selected.Text), 
Filter(dataSource, jobNumberColumn = cbJobNumber.Selected.Text),
Notify("Either JobNumber or Address is required", Error))
```
###
***
<b><u>OnCheck Property </u></b>
```Excel
ClearCollect(
    	SelectedEquipment,
    		If(CheckboxYes.Value,"Yes"),
    		If(CheckboxNo.Value,"No"),
    		If(CheckboxMaybe.Value,"Maybe")
    );
    ClearCollect(
    	SelectedEquipment,Filter(
    		SelectedEquipment,
    		!IsBlank(Value)
    	)
    )
```
###
***
<b><u>OnUncheck Property </u></b>
```Excel
ClearCollect(
    	SelectedEquipment,
    		If(CheckboxYes.Value,"Yes"),
    		If(CheckboxNo.Value,"No"),
    		If(CheckboxMaybe.Value,"Maybe")
    );
    ClearCollect(
    	SelectedEquipment,Filter(
    		SelectedEquipment,
    		!IsBlank(Value)
    	)
    )
```
###
***
<b><u>Concatenate using 2 column </u></b>
```Excel
Distinct(
    Filter(
        'SharePointListData',
        SubCategory = SubCategoryDrp.Selected.Result
    ),
    Concatenate(
        Item,
        ", ",
        ProductName
    )
)
```
