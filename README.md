<div align="center">

## Add new item in System Menu


</div>

### Description

A simple way to add new items in your application's system menu or delete current items,see screenshot to understand or right click on your application's button in taskbar. Please Vote...Thanx :)
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Nicholas Afxentiou](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/nicholas-afxentiou.md)
**Level**          |Intermediate
**User Rating**    |4.7 (56 globes from 12 users)
**Compatibility**  |VB\.NET
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__10-1.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/nicholas-afxentiou-add-new-item-in-system-menu__10-1519/archive/master.zip)





### Source Code

```
'declarations
Private Declare Function GetSystemMenu Lib "user32" (ByVal hwnd As Integer, ByVal bRevert As Boolean) As Integer
 Private Declare Function AppendMenu Lib "user32" Alias "AppendMenuA" (ByVal hMenu As Integer, ByVal wFlags As Integer, ByVal wIDNewItem As Integer, ByVal lpNewItem As String) As Integer
Private Declare Function RemoveMenu Lib "user32" (ByVal hMenu As Long, ByVal nPosition As Long, ByVal wFlags As Long) As Long
Const MF_BYPOSITION = &H400&
Const MF_REMOVE = &H1000&
 Const WM_SYSCOMMAND As Integer = &H112
'-----------------------------------
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load
 Dim hSysMenu As Integer
 hSysMenu = GetSystemMenu(Me.Handle.ToInt32, False)
'deletes the close menu item which is in place 6
RemoveMenu(hSysMenu, 6, MF_REMOVE)
'appends new menu items
 AppendMenu(hSysMenu, 0, 1000, "New Item1")
 AppendMenu(hSysMenu, 0, 1001, "New Item2")
 End Sub
'--------------------------------
Protected Overrides Sub WndProc(ByRef m As Message)
 MyBase.WndProc(m)
 If m.Msg = WM_SYSCOMMAND Then
 Select Case m.WParam.ToInt32
 Case 1000
  MsgBox("Hello1")
 Case 1001
  MsgBox("Hello2")
 End Select
 End If
 End Sub
```

