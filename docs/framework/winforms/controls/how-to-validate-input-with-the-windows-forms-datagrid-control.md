---
title: 'Nasıl yapılır: Windows Forms DataGrid denetimiyle girişi doğrulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid control [Windows Forms], examples
- user input [Windows Forms], validating
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], validating input
- validation [Windows Forms], user input
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
ms.openlocfilehash: 84057a2d9709963c7a7302110ab11931b86fcad9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497632"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid denetimiyle girişi doğrulama

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

İki tür giriş doğrulaması Windows Forms'da kullanılabilen <xref:System.Windows.Forms.DataGrid> denetimi. Kullanıcı bir kabul edilebilir veri türü tamsayı, örneğin bir dizeye hücre için bir değer girmeyi denerse yeni geçersiz bir değer eski değer ile değiştirilir. Bu tür bir giriş doğrulama otomatik olarak yapılır ve özelleştirilemez.

Bir giriş doğrulama türünü kabul edilemez tüm verileri, örneğin 0 değerinde büyüktür veya eşittir 1 ya da uygun olmayan bir dize olmalıdır. bir alan reddetmek için kullanılabilir. Bu veri kümesi için bir olay işleyicisi yazarak yapılır <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay. Kullanan aşağıdaki örnekte <xref:System.Data.DataTable.ColumnChanging> olay "Product" sütunu için özellikle izin verilmeyen kabul edilemez değeri olduğundan. Kullanabileceğinize <xref:System.Data.DataTable.RowChanging> bir "Bitiş tarihi" sütunun değeri "StartDate" sütun ile aynı satırdaki daha olduğunu denetlemek için olay.

## <a name="to-validate-user-input"></a>Kullanıcı girişini doğrulamak için

1. İşlemek için kod yazma <xref:System.Data.DataTable.ColumnChanging> uygun tablosu için olay. Uygun olmayan giriş algılandığında, çağrı <xref:System.Data.DataRow.SetColumnError%2A> yöntemi <xref:System.Data.DataRow> nesne.

    ```vb
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _
    ByVal e As System.Data.DataColumnChangeEventArgs)
       ' Only check for errors in the Product column
       If (e.Column.ColumnName.Equals("Product")) Then
          ' Do not allow "Automobile" as a product.
          If CType(e.ProposedValue, String) = "Automobile" Then
             Dim badValue As Object = e.ProposedValue
             e.ProposedValue = "Bad Data"
             e.Row.RowError = "The Product column contains an error"
             e.Row.SetColumnError(e.Column, "Product cannot be " & _
             CType(badValue, String))
          End If
       End If
    End Sub
    ```

    ```csharp
    //Handle column changing events on the Customers table
    private void Customers_ColumnChanging(object sender, System.Data.DataColumnChangeEventArgs e) {

       //Only check for errors in the Product column
       if (e.Column.ColumnName.Equals("Product")) {

          //Do not allow "Automobile" as a product
          if (e.ProposedValue.Equals("Automobile")) {
             object badValue = e.ProposedValue;
             e.ProposedValue = "Bad Data";
             e.Row.RowError = "The Product column contains an error";
             e.Row.SetColumnError(e.Column, "Product cannot be " + badValue);
          }
       }
    }
    ```

2. Olay işleyicisi olaya bağlayın.

    Yere aşağıdaki kod içinde ya da formun <xref:System.Windows.Forms.Form.Load> olay ya da kendi Oluşturucu.

    ```vb
    ' Assumes the grid is bound to a dataset called customersDataSet1
    ' with a table called Customers.
    ' Put this code in the form's Load event or its constructor.
    AddHandler customersDataSet1.Tables("Customers").ColumnChanging, AddressOf Customers_ColumnChanging
    ```

    ```csharp
    // Assumes the grid is bound to a dataset called customersDataSet1
    // with a table called Customers.
    // Put this code in the form's Load event or its constructor.
    customersDataSet1.Tables["Customers"].ColumnChanging += new DataColumnChangeEventHandler(this.Customers_ColumnChanging);
    ```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
