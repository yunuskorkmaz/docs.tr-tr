---
description: 'Daha fazla bilgi edinin: satır hatası bilgileri'
title: Satır Hatası Bilgileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: d3eb8b20893ad47720ebb03ad4ab61940f014bd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651697"
---
# <a name="row-error-information"></a><span data-ttu-id="6723c-103">Satır Hatası Bilgileri</span><span class="sxs-lookup"><span data-stu-id="6723c-103">Row Error Information</span></span>

<span data-ttu-id="6723c-104">İçindeki değerleri düzenlenirken satır hatalarına yanıt vermekten kaçınmak için <xref:System.Data.DataTable> , daha sonra kullanmak üzere satıra hata bilgilerini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6723c-104">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="6723c-105"><xref:System.Data.DataRow>Nesnesi <xref:System.Data.DataRow.RowError%2A> Bu amaçla her satırda bir özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="6723c-105">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="6723c-106">Bir **DataRow** 'ın **RowError** özelliğine veri eklemek <xref:System.Data.DataRow.HasErrors%2A> , **DataRow** 'ın özelliğini **true** olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6723c-106">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="6723c-107">**DataRow** bir **DataTable**'ın parçasıysa ve **DataRow. HasErrors** **true** ise, **DataTable. HasErrors** özelliği de **doğrudur**.</span><span class="sxs-lookup"><span data-stu-id="6723c-107">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="6723c-108">Bu, **DataTable** 'ın ait olduğu **veri kümesine** de uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6723c-108">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="6723c-109">Hatalar için test edilirken **HasErrors** özelliğini denetleyerek herhangi bir satıra hata bilgilerinin eklenip eklenmediğine bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6723c-109">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="6723c-110">**HasErrors** **true** ise, <xref:System.Data.DataTable.GetErrors%2A> Aşağıdaki örnekte gösterildiği gibi, yalnızca hataları olan satırları döndürmek ve incelemek için **DataTable** 'ın yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6723c-110">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6723c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6723c-111">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="6723c-112">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="6723c-112">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="6723c-113">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6723c-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
