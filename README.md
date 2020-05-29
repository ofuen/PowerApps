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
###
***
<b><u>Remove Function - items property </u></b>
```Excel
Remove(myCollection, GalleryName.Selected)
or
Remove(myCollection, ThisItem)
```
###
***
<b><u>Validate Form and Gallery </u></b>
```Excel
If(
    !Form2.Valid,
    SubmitForm(Form2),
    ForAll(
        Gallery1.AllItems,
        Patch(
            'Pitney Bowes Order',
            Defaults('Pitney Bowes Order'),
            Form2.Updates,
            {Category: TextInput1.Text},
            {SubCategory: TextInput1_1.Text},
            {ProductName: TextInput1_2.Text},
            {Quantity: TextInput3.Text}
        )
    )
)
```
***
<b><u>Validate DOB in PowerApps</u></b>
  ```Javascript
  If(
   !IsMatch(Text(DataCardValue17.SelectedDate), "\d{1,2}/\d{1,2}/\d{4}") || Value(First(Split(Text(DataCardValue17.SelectedDate), "/")).Result)>12 || Value(Last(FirstN(Split(Text(DataCardValue17.SelectedDate), "/"))).Result)>31, 
   Notify("The date value you typed within the Date Picker control is in wrong format. The correct format is mm/dd/yyyy.", NotificationType.Error), 
   Notify("Right Date format",NotificationType.Success, 2000)
)
```
***
