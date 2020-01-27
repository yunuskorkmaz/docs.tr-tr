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
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="7a77f-102">Nasıl yapılır: Windows Forms DataGrid Denetimiyle Girişi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="7a77f-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>

> [!NOTE]
> <span data-ttu-id="7a77f-103"><xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="7a77f-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="7a77f-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7a77f-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

<span data-ttu-id="7a77f-105">Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi için kullanılabilen iki tür giriş doğrulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="7a77f-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="7a77f-106">Kullanıcı hücre için kabul edilemez bir veri türünde bir değer girmeyi denerse (örneğin, bir tamsayı), yeni geçersiz değer eski değer ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7a77f-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="7a77f-107">Bu tür bir giriş doğrulaması otomatik olarak yapılır ve özelleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="7a77f-107">This kind of input validation is done automatically and cannot be customized.</span></span>

<span data-ttu-id="7a77f-108">Diğer giriş doğrulaması türü, kabul edilmeyen verileri reddetmek için kullanılabilir (örneğin, 1 ' den büyük veya buna eşit veya uygun olmayan bir dize) bir alanda 0 değeri.</span><span class="sxs-lookup"><span data-stu-id="7a77f-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="7a77f-109">Bu, <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olayı için bir olay işleyicisi yazılarak veri kümesinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="7a77f-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="7a77f-110">Aşağıdaki örnek, "Product" sütunu için kabul edilemez değere izin verilmediğinden <xref:System.Data.DataTable.ColumnChanging> olayını kullanır.</span><span class="sxs-lookup"><span data-stu-id="7a77f-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="7a77f-111">Bir "bitiş tarihi" sütununun değerinin aynı satırdaki "başlangıç tarihi" sütunundan daha geç olduğunu denetlemek için <xref:System.Data.DataTable.RowChanging> olayını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a77f-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>

## <a name="to-validate-user-input"></a><span data-ttu-id="7a77f-112">Kullanıcı girişini doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="7a77f-112">To validate user input</span></span>

1. <span data-ttu-id="7a77f-113">Uygun tablo için <xref:System.Data.DataTable.ColumnChanging> olayını işlemek üzere kod yazın.</span><span class="sxs-lookup"><span data-stu-id="7a77f-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="7a77f-114">Uygunsuz giriş algılandığında, <xref:System.Data.DataRow> nesnesinin <xref:System.Data.DataRow.SetColumnError%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="7a77f-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>

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

2. <span data-ttu-id="7a77f-115">Olay işleyicisini olaya bağlayın.</span><span class="sxs-lookup"><span data-stu-id="7a77f-115">Connect the event handler to the event.</span></span>

    <span data-ttu-id="7a77f-116">Aşağıdaki kodu formun <xref:System.Windows.Forms.Form.Load> olayının veya oluşturucusunun içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="7a77f-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7a77f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a77f-117">See also</span></span>

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [<span data-ttu-id="7a77f-118">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="7a77f-118">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
