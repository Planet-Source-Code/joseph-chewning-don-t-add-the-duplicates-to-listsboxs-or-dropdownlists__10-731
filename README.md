<div align="center">

## Don't add the Duplicates to Listsboxs or DropDownLists


</div>

### Description

This code will connect to an Oracle Database and automatically add items to a list control (i.e. DropDownList and Listboxes) and will not generate duplicates. You can modify the code to hit other types of databases. --Have Fun !--
 
### More Info
 
'none

need to point the connection string to your database. This is an Oracle connection so you may have to change the type of connection. Change the name of the control.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Joseph Chewning](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/joseph-chewning.md)
**Level**          |Beginner
**User Rating**    |4.1 (29 globes from 7 users)
**Compatibility**  |VB\.NET, ASP\.NET
**Category**       |[Controls/ Forms/ Dialogs/ Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/controls-forms-dialogs-menus__10-3.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/joseph-chewning-don-t-add-the-duplicates-to-listsboxs-or-dropdownlists__10-731/archive/master.zip)

### API Declarations

```
'none
```


### Source Code

```
Sub LoadList()
yourlistcontrolname.Items.Clear() 'Want to make it fresh
    Dim ds As New ListItem()
    Dim cConnString As String = "Provider=MSDAORA;Data Source="need to add your source";User ID="add your user name";Password="add your password"" 'connection string to Oracle Database
    Dim cn As New OleDbConnection(cConnString)
    Dim Sql As String = "SELECT LOCATION, CHEMICAL_NAME FROM TC_INVENTORY"
    Dim daCmd5 As New OleDbCommand(Sql, cn)
    cn.Open()
    Dim datinfo As OleDbDataReader = daCmd5.ExecuteReader() 'build the reader
    While datinfo.Read() 'start looping through the records
      ds.Text = datinfo(0) 'This will load the "LOCATION" part of the Sql Statement into the control
      If yourlistcontrolname.Items.Contains(ds) = False Then 'if they are not equal add it
        yourlistcontrolname.Items.Add(datinfo(0))
      End If
    End While
    cn.Close()
End Sub
```

