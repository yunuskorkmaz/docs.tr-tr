---
title: DataGrid denetimiyle girişi doğrulama
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
ms.openlocfilehash: 3958089007401d2e977c9c96f07c9196e6216596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728290"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimiyle Girişi Doğrulama

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi için kullanılabilen iki tür giriş doğrulaması vardır. Kullanıcı hücre için kabul edilemez bir veri türünde bir değer girmeyi denerse (örneğin, bir tamsayı), yeni geçersiz değer eski değer ile değiştirilmiştir. Bu tür bir giriş doğrulaması otomatik olarak yapılır ve özelleştirilemez.

Diğer giriş doğrulaması türü, kabul edilmeyen verileri reddetmek için kullanılabilir (örneğin, 1 ' den büyük veya buna eşit veya uygun olmayan bir dize) bir alanda 0 değeri. Bu, <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olayı için bir olay işleyicisi yazılarak veri kümesinde yapılır. Aşağıdaki örnek, "Product" sütunu için kabul edilemez değere izin verilmediğinden <xref:System.Data.DataTable.ColumnChanging> olayını kullanır. Bir "bitiş tarihi" sütununun değerinin aynı satırdaki "başlangıç tarihi" sütunundan daha geç olduğunu denetlemek için <xref:System.Data.DataTable.RowChanging> olayını kullanabilirsiniz.

## <a name="to-validate-user-input"></a>Kullanıcı girişini doğrulamak için

1. Uygun tablo için <xref:System.Data.DataTable.ColumnChanging> olayını işlemek üzere kod yazın. Uygunsuz giriş algılandığında, <xref:System.Data.DataRow> nesnesinin <xref:System.Data.DataRow.SetColumnError%2A> yöntemini çağırın.

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

2. Olay işleyicisini olaya bağlayın.

    Aşağıdaki kodu formun <xref:System.Windows.Forms.Form.Load> olayının veya oluşturucusunun içine yerleştirin.

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
- [DataGrid Denetimi](datagrid-control-windows-forms.md)
