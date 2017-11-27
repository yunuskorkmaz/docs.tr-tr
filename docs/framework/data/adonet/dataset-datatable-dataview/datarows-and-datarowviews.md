---
title: DataRow ve DataRowView
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e342ce805880da848da1e17700c055aba2c74f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="4cb11-102">DataRow ve DataRowView</span><span class="sxs-lookup"><span data-stu-id="4cb11-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="4cb11-103">A <xref:System.Data.DataView> numaralandırılabilir bir topluluğu gösterir <xref:System.Data.DataRowView> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4cb11-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="4cb11-104">**DataRowView** nesneleri adını veya temel tablodaki sütun sıralı başvurusu tarafından dizine nesne dizileri olarak değerleri kullanıma.</span><span class="sxs-lookup"><span data-stu-id="4cb11-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="4cb11-105">Erişebileceğiniz <xref:System.Data.DataRow> tarafından sunulan **DataRowView** kullanarak <xref:System.Data.DataRowView.Row%2A> özelliği **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="4cb11-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="4cb11-106">Kullanarak değerleri görüntülerken bir **DataRowView**, <xref:System.Data.DataView.RowStateFilter%2A> özelliği **DataView** temel hangi satır sürümü belirler **DataRow** sunulur.</span><span class="sxs-lookup"><span data-stu-id="4cb11-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="4cb11-107">Kullanarak farklı satır sürümler erişme hakkında bilgi için bir **DataRow**, bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="4cb11-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="4cb11-108">Aşağıdaki kod örneği, bir tablodaki tüm geçerli ve özgün değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4cb11-108">The following code example displays all the current and original values in a table.</span></span>  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)      
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cb11-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4cb11-109">See Also</span></span>  
 <xref:System.Data.DataRowVersion>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="4cb11-110">DataView</span><span class="sxs-lookup"><span data-stu-id="4cb11-110">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="4cb11-111">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="4cb11-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
