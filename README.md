<p align="center">
<img src="https://user-images.githubusercontent.com/19554935/66256981-bc639e80-e761-11e9-8f6c-03e461718035.png"/>
  </p>
  
  
***
### `PowerApps Formulas`
***

<details> 
  <summary><b>Toggle</b></summary>
 <br>
  
```JavaScript
If(Toggle1.Value=true, true, false)
```
</details>


<details>
  <summary><b>Yes/No</b></summary>
  <br>
  
```JavaScript
If(DataCardValue*.Value=true, true, false)
```
</details>


<details>
  <summary><b>If Toggle value is NO, N/A will be fill</b></summary>
  <br>
  
```JavaScript
If(!(DataCardValue20),"N/A",Parent.Default)
```
</details>

<details>
  <summary><b>Default Property → Fill in N/A for Required field</summary>
    <br>
    
```JavaScript
If(!(DataCardValue37),"N/A",Parent.Default)
```
</details>

<details>
  <summary>How to make two combo box search to display the content and vice versa</summary>
  <br>
  
```JavaScript
If(!IsBlank(cbAddress.Selected.Text), 
Filter(dataSource, addressColumn = cbAddress.Selected.Text), 
!IsBlank(cbJobNumber.Selected.Text), 
Filter(dataSource, jobNumberColumn = cbJobNumber.Selected.Text),
Notify("Either JobNumber or Address is required", Error))
```
</details>

##### `OnCheck Property` #####
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
##### `OnUncheck Property` #####
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
##### `Concatenate using 2 column` #####
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
##### `Remove Function - items property` #####
```JavaScript
Remove(myCollection, GalleryName.Selected)
or
Remove(myCollection, ThisItem)
```
###
***
##### `Validate Form and Gallery` #####
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
##### `Validate DOB in PowerApps` #####
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
