---
title: "Nasıl yapılır: Windows Forms DataGrid Denetimiyle Girişi Doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f5e0c366f71f602be2bb1508a6abb00d3d0c83ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Nasıl yapılır: Windows Forms DataGrid Denetimiyle Girişi Doğrulama
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 İki tür giriş doğrulaması Windows Forms için kullanılabilir <xref:System.Windows.Forms.DataGrid> denetim. Kullanıcı hücrenin, tamsayı, örneğin bir dizeye bir kabul edilebilir veri türünde bir değer girmesini çalışırsa yeni geçersiz değer eski değer ile değiştirilir. Bu tür bir giriş doğrulaması otomatik olarak yapılır ve özelleştirilemez.  
  
 Giriş doğrulaması başka türden herhangi bir kabul edilebilir veri, örneğin 0 değeri sıfırdan büyük veya eşittir 1 ya da uygun olmayan bir dize olmalıdır bir alandaki reddetmek için kullanılır. Bu veri kümesini için bir olay işleyicisi yazarak yapılır <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay. Kullandığı aşağıdaki örnekte <xref:System.Data.DataTable.ColumnChanging> olay "Ürün" sütunu için özellikle izin verilmeyen kabul edilebilir değer olduğundan. Kullanabileceğinize <xref:System.Data.DataTable.RowChanging> bir "Bitiş tarihi" sütunun değeri daha sonraki bir satıra "Başlangıç tarihi" sütununda olduğunu denetlemek için olay.  
  
### <a name="to-validate-user-input"></a>Kullanıcı girişi doğrulamak için  
  
1.  İşlemek için kod yazma <xref:System.Data.DataTable.ColumnChanging> uygun tablosu için olay. Uygunsuz giriş algılandığında, çağrı <xref:System.Data.DataRow.SetColumnError%2A> yöntemi <xref:System.Data.DataRow> nesnesi.  
  
    ```vb  
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _  
    ByVal e As System.Data.DataColumnChangeEventArgs)  
       ' Only check for errors in the Product column  
       If (e.Column.ColumnName.Equals("Product")) Then  
          ' Do not allow "Automobile" as a product.  
          If CType(e.ProposedValue, String) = "Automobile" Then  
             Dim badValue As Object = e.ProposedValue  
             e.ProposedValue = "Bad Data"  
             e.Row.RowError = "The Product column contians an error"  
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
  
2.  Olay işleyicisi olaya bağlayın.  
  
     Yere aşağıdaki kod içinde ya da formun <xref:System.Windows.Forms.Form.Load> olay ya da kendi Oluşturucusu.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Data.DataTable.ColumnChanging>  
 <xref:System.Data.DataRow.SetColumnError%2A>  
 [DataGrid denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
