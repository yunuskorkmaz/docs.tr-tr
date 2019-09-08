---
title: Satır Hatası Bilgileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 5ede6e2cd52ad55f8c35a42d137044dd1ceea400
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785960"
---
# <a name="row-error-information"></a>Satır Hatası Bilgileri
İçindeki değerleri düzenlenirken satır hatalarına yanıt vermekten kaçınmak için <xref:System.Data.DataTable>, daha sonra kullanmak üzere satıra hata bilgilerini ekleyebilirsiniz. Nesnesi bu amaçla her <xref:System.Data.DataRow.RowError%2A> satırda bir özellik sağlar. <xref:System.Data.DataRow> Bir **DataRow** <xref:System.Data.DataRow.HasErrors%2A> 'ın **RowError** özelliğine veri eklemek, **DataRow** 'ın özelliğini **true**olarak ayarlar. **DataRow** bir **DataTable**'ın parçasıysa ve **DataRow. HasErrors** **true**ise, **DataTable. HasErrors** özelliği de **doğrudur**. Bu, **DataTable** 'ın ait olduğu **veri kümesine** de uygulanır. Hatalar için test edilirken **HasErrors** özelliğini denetleyerek herhangi bir satıra hata bilgilerinin eklenip eklenmediğine bakabilirsiniz. **HasErrors** **true**ise, aşağıdaki örnekte gösterildiği gibi, <xref:System.Data.DataTable.GetErrors%2A> yalnızca hataları olan satırları döndürmek ve incelemek için **DataTable** 'ın yöntemini kullanabilirsiniz.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
