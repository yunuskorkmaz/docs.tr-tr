---
title: 'Nasıl yapılır: Windows Forms DataGrid Denetiminde Tıklamalara Yanıt Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Click event [Windows Forms], monitoring in DataGrid controls
- DataGrid control [Windows Forms], examples
- DataGrid control [Windows Forms], returning clicked cell value
- cells [Windows Forms], location in DataGrid
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], click events
ms.assetid: a0aa204b-8351-4d82-9933-ee21a5c9e409
ms.openlocfilehash: 60c4dac76b4a7868da9143cab1433ee93f97c7d1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64636804"
---
# <a name="how-to-respond-to-clicks-in-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetiminde Tıklamalara Yanıt Verme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms sonra <xref:System.Windows.Forms.DataGrid> bağlı bir veritabanı için kullanıcının tıklanan hücre izleyebilirsiniz.  
  
### <a name="to-detect-when-the-user-of-the-datagrid-selects-a-different-cell"></a>DataGrid kullanıcı farklı bir hücre seçtiğinde algılamak için  
  
- İçinde <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> olay işleyicisi, uygun şekilde yanıt vermek için kod yazın.  
  
    ```vb  
    Private Sub myDataGrid_CurrentCellChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles myDataGrid.CurrentCellChanged  
       MessageBox.Show("Col is " & myDataGrid.CurrentCell.ColumnNumber _  
          & ", Row is " & myDataGrid.CurrentCell.RowNumber _  
          & ", Value is " & myDataGrid.Item(myDataGrid.CurrentCell))  
    End Sub  
    ```  
  
    ```csharp  
    private void myDataGrid_CurrentCellChanged(object sender,   
    System.EventArgs e)  
    {  
       MessageBox.Show ("Col is " + myDataGrid.CurrentCell.ColumnNumber  
          + ", Row is " + myDataGrid.CurrentCell.RowNumber   
          + ", Value is " + myDataGrid[myDataGrid.CurrentCell] );  
    }  
    ```  
  
     (Visual C#) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
    ```csharp  
    this.myDataGrid.CurrentCellChanged += new  
       System.EventHandler(this.myDataGrid_CurrentCellChanged);  
    ```  
  
### <a name="to-determine-which-part-of-the-datagrid-the-user-clicked"></a>Kullanıcı hangi kısmını DataGrid tıkladı belirlemek için  
  
- Çağrı <xref:System.Windows.Forms.DataGrid.HitTest%2A> uygun olay işleyicisi, gibi yönteminde <xref:System.Windows.Forms.Control.MouseDown> veya <xref:System.Windows.Forms.Control.Click> olay.  
  
     <xref:System.Windows.Forms.DataGrid.HitTest%2A> Yöntemi döndürür bir <xref:System.Windows.Forms.DataGrid.HitTestInfo> satır ve sütunları tıklandı alanı içeren nesne.  
  
    ```vb  
    Private Sub myDataGrid_MouseDown(ByVal sender As Object, _  
    ByVal e As MouseEventArgs) Handles myDataGrid.MouseDown  
       Dim myGrid As DataGrid = CType(sender, DataGrid)  
       Dim hti As System.Windows.Forms.DataGrid.HitTestInfo  
       hti = myGrid.HitTest(e.X, e.Y)  
       Dim message As String = "You clicked "  
  
       Select Case hti.Type  
          Case System.Windows.Forms.DataGrid.HitTestType.None  
             message &= "the background."  
          Case System.Windows.Forms.DataGrid.HitTestType.Cell  
             message &= "cell at row " & hti.Row & ", col " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.ColumnHeader  
             message &= "the column header for column " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.RowHeader  
             message &= "the row header for row " & hti.Row  
          Case System.Windows.Forms.DataGrid.HitTestType.ColumnResize  
             message &= "the column resizer for column " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.RowResize  
             message &= "the row resizer for row " & hti.Row  
          Case System.Windows.Forms.DataGrid.HitTestType.Caption  
             message &= "the caption"  
          Case System.Windows.Forms.DataGrid.HitTestType.ParentRows  
             message &= "the parent row"  
       End Select  
  
       Console.WriteLine(message)  
    End Sub  
    ```  
  
    ```csharp  
    private void myDataGrid_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       DataGrid myGrid = (DataGrid) sender;  
       System.Windows.Forms.DataGrid.HitTestInfo hti;  
       hti = myGrid.HitTest(e.X, e.Y);  
       string message = "You clicked ";  
  
       switch (hti.Type)   
       {  
          case System.Windows.Forms.DataGrid.HitTestType.None :  
             message += "the background.";  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.Cell :  
             message += "cell at row " + hti.Row + ", col " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ColumnHeader :  
             message += "the column header for column " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.RowHeader :  
             message += "the row header for row " + hti.Row;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ColumnResize :  
             message += "the column resizer for column " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.RowResize :  
             message += "the row resizer for row " + hti.Row;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.Caption :  
             message += "the caption";  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ParentRows :  
             message += "the parent row";  
             break;  
          }  
  
          Console.WriteLine(message);  
    }  
    ```  
  
     (Visual C#) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
    ```csharp  
    this.myDataGrid.MouseDown += new  
       System.Windows.Forms.MouseEventHandler  
       (this.myDataGrid_MouseDown);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetiminde çalışma zamanında görüntülenen verileri değiştirme](change-displayed-data-at-run-time-wf-datagrid-control.md)
