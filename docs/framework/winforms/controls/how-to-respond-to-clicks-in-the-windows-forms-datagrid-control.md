---
title: DataGrid Denetimindeki Tıklamalara Yanıt Ver
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
ms.openlocfilehash: e72d117b12d43ece8c4d05ed29ab45693418eede
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141945"
---
# <a name="how-to-respond-to-clicks-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="38c21-102">Nasıl yapılır: Windows Forms DataGrid Denetiminde Tıklamalara Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="38c21-102">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="38c21-103">Denetim, <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGrid> yerini alır ve işlevsellik ekler; ancak, <xref:System.Windows.Forms.DataGrid> isterseniz, denetim hem geriye dönük uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="38c21-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="38c21-104">Daha fazla bilgi için [Bkz. Windows Formları DataGridView ve DataGrid Denetimleri arasındaki farklar.](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)</span><span class="sxs-lookup"><span data-stu-id="38c21-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="38c21-105">Windows Formları <xref:System.Windows.Forms.DataGrid> bir veritabanına bağlandıktan sonra, kullanıcının hangi hücreyi tıklattıklarını izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38c21-105">After the Windows Forms <xref:System.Windows.Forms.DataGrid> is connected to a database, you can monitor which cell the user clicked.</span></span>  
  
### <a name="to-detect-when-the-user-of-the-datagrid-selects-a-different-cell"></a><span data-ttu-id="38c21-106">DataGrid kullanıcısının farklı bir hücre seçtiğini tespit etmek için</span><span class="sxs-lookup"><span data-stu-id="38c21-106">To detect when the user of the DataGrid selects a different cell</span></span>  
  
- <span data-ttu-id="38c21-107">Olay <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> işleyicisi, uygun yanıt için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="38c21-107">In the <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> event handler, write code to respond appropriately.</span></span>  
  
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
  
     <span data-ttu-id="38c21-108">(Görsel C#) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="38c21-108">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.myDataGrid.CurrentCellChanged += new  
       System.EventHandler(this.myDataGrid_CurrentCellChanged);  
    ```  
  
### <a name="to-determine-which-part-of-the-datagrid-the-user-clicked"></a><span data-ttu-id="38c21-109">DataGrid'in hangi bölümünü tıkladığına karar vermek için</span><span class="sxs-lookup"><span data-stu-id="38c21-109">To determine which part of the DataGrid the user clicked</span></span>  
  
- <span data-ttu-id="38c21-110"><xref:System.Windows.Forms.DataGrid.HitTest%2A> Yöntemi, olay veya <xref:System.Windows.Forms.Control.Click> olay gibi uygun bir olay işleyicisi <xref:System.Windows.Forms.Control.MouseDown> olarak çağırın.</span><span class="sxs-lookup"><span data-stu-id="38c21-110">Call the <xref:System.Windows.Forms.DataGrid.HitTest%2A> method in an appropriate event handler, such as for the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     <span data-ttu-id="38c21-111">Yöntem, <xref:System.Windows.Forms.DataGrid.HitTest%2A> tıklatılmış bir <xref:System.Windows.Forms.DataGrid.HitTestInfo> alanın satır ve sütununu içeren bir nesneyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="38c21-111">The <xref:System.Windows.Forms.DataGrid.HitTest%2A> method returns a <xref:System.Windows.Forms.DataGrid.HitTestInfo> object that contains the row and column of a clicked area.</span></span>  
  
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
  
     <span data-ttu-id="38c21-112">(Görsel C#) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="38c21-112">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.myDataGrid.MouseDown += new  
       System.Windows.Forms.MouseEventHandler  
       (this.myDataGrid_MouseDown);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="38c21-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38c21-113">See also</span></span>

- [<span data-ttu-id="38c21-114">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="38c21-114">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="38c21-115">Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="38c21-115">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
