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
ms.workload: dotnet
ms.openlocfilehash: 88cdc7914c301af0f0f244f935b986fb78ec775e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="cf389-102">Nasıl yapılır: Windows Forms DataGrid Denetimiyle Girişi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="cf389-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="cf389-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="cf389-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="cf389-104">Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cf389-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="cf389-105">İki tür giriş doğrulaması Windows Forms için kullanılabilir <xref:System.Windows.Forms.DataGrid> denetim.</span><span class="sxs-lookup"><span data-stu-id="cf389-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="cf389-106">Kullanıcı hücrenin, tamsayı, örneğin bir dizeye bir kabul edilebilir veri türünde bir değer girmesini çalışırsa yeni geçersiz değer eski değer ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="cf389-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="cf389-107">Bu tür bir giriş doğrulaması otomatik olarak yapılır ve özelleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="cf389-107">This kind of input validation is done automatically and cannot be customized.</span></span>  
  
 <span data-ttu-id="cf389-108">Giriş doğrulaması başka türden herhangi bir kabul edilebilir veri, örneğin 0 değeri sıfırdan büyük veya eşittir 1 ya da uygun olmayan bir dize olmalıdır bir alandaki reddetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf389-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="cf389-109">Bu veri kümesini için bir olay işleyicisi yazarak yapılır <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay.</span><span class="sxs-lookup"><span data-stu-id="cf389-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="cf389-110">Kullandığı aşağıdaki örnekte <xref:System.Data.DataTable.ColumnChanging> olay "Ürün" sütunu için özellikle izin verilmeyen kabul edilebilir değer olduğundan.</span><span class="sxs-lookup"><span data-stu-id="cf389-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="cf389-111">Kullanabileceğinize <xref:System.Data.DataTable.RowChanging> bir "Bitiş tarihi" sütunun değeri daha sonraki bir satıra "Başlangıç tarihi" sütununda olduğunu denetlemek için olay.</span><span class="sxs-lookup"><span data-stu-id="cf389-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>  
  
### <a name="to-validate-user-input"></a><span data-ttu-id="cf389-112">Kullanıcı girişi doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="cf389-112">To validate user input</span></span>  
  
1.  <span data-ttu-id="cf389-113">İşlemek için kod yazma <xref:System.Data.DataTable.ColumnChanging> uygun tablosu için olay.</span><span class="sxs-lookup"><span data-stu-id="cf389-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="cf389-114">Uygunsuz giriş algılandığında, çağrı <xref:System.Data.DataRow.SetColumnError%2A> yöntemi <xref:System.Data.DataRow> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cf389-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>  
  
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
  
2.  <span data-ttu-id="cf389-115">Olay işleyicisi olaya bağlayın.</span><span class="sxs-lookup"><span data-stu-id="cf389-115">Connect the event handler to the event.</span></span>  
  
     <span data-ttu-id="cf389-116">Yere aşağıdaki kod içinde ya da formun <xref:System.Windows.Forms.Form.Load> olay ya da kendi Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="cf389-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf389-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf389-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Data.DataTable.ColumnChanging>  
 <xref:System.Data.DataRow.SetColumnError%2A>  
 [<span data-ttu-id="cf389-118">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="cf389-118">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
