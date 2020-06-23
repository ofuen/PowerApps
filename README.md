<p align="center">
<img src="https://user-images.githubusercontent.com/19554935/66256981-bc639e80-e761-11e9-8f6c-03e461718035.png"/>
  </p>
  
  
***
### `PowerApps Formulas`
***
##
# `Toggle` #
```JavaScript
If(Toggle1.Value=true, true, false)
```
##
## :white_check_mark: `Yes/No` ##
```JavaScript
If(DataCardValue*.Value=true, true, false)
```
##
***
##
# If Toggle value is NO, N/A will be fill #
```JavaScript
If(!(DataCardValue20),"N/A",Parent.Default)
```
##
***
<b><u>Default Property → Fill in N/A for Required field</u></b>
```JavaScript
If(!(DataCardValue37),"N/A",Parent.Default)
```
###
***
<b><u>How to make two combo box search to display the content and vice versa</u></b>
```JavaScript
If(!IsBlank(cbAddress.Selected.Text), 
Filter(dataSource, addressColumn = cbAddress.Selected.Text), 
!IsBlank(cbJobNumber.Selected.Text), 
Filter(dataSource, jobNumberColumn = cbJobNumber.Selected.Text),
Notify("Either JobNumber or Address is required", Error))
```
###
***
<b><u>OnCheck Property </u></b>
```JavaScript
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
```JavaScript
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
```JavaScript
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
```JavaScript
Remove(myCollection, GalleryName.Selected)
or
Remove(myCollection, ThisItem)
```
###
***
<b><u>Validate Form and Gallery </u></b>
```JavaScript
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
***
![image](https://user-images.githubusercontent.com/19554935/83313399-0b27e200-a1e4-11ea-9098-03c6a1dbc0f8.png)
![image](https://user-images.githubusercontent.com/19554935/83313439-2bf03780-a1e4-11ea-9fad-cb3afdf87cf2.png)
***
  ```Javascript
  If(
   !IsMatch(Text(DataCardValue17.SelectedDate), "\d{1,2}/\d{1,2}/\d{4}") || Value(First(Split(Text(DataCardValue17.SelectedDate), "/")).Result)>12 || Value(Last(FirstN(Split(Text(DataCardValue17.SelectedDate), "/"))).Result)>31, 
   Notify("The date value you typed within the Date Picker control is in wrong format. The correct format is mm/dd/yyyy.", NotificationType.Error), 
   Notify("Right Date format",NotificationType.Success, 2000)
)
```
***
