---
title: DataRows ve DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 14e7e1ccb051410c351e49afee9f2d6809264833
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151305"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="aeaab-102">DataRows ve DataRowViews</span><span class="sxs-lookup"><span data-stu-id="aeaab-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="aeaab-103">A, <xref:System.Data.DataView> sayısal bir <xref:System.Data.DataRowView> nesne koleksiyonunu ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="aeaab-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="aeaab-104">**DataRowView** nesneleri, alttaki tablodaki sütunun adı veya ordinal başvurusu tarafından dizilen nesne dizileri olarak değerleri ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="aeaab-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="aeaab-105"><xref:System.Data.DataRow> **DataRowView'ın**özelliğini <xref:System.Data.DataRowView.Row%2A> kullanarak **DataRowView** tarafından ortaya çıkarılanlara erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aeaab-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="aeaab-106">**Verileri Bir DataRowView**kullanarak görüntülediğinizde, **DataView'ın** <xref:System.Data.DataView.RowStateFilter%2A> özelliği, alttaki **DataRow'un** hangi satır sürümünün açıkta olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="aeaab-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="aeaab-107">**Bir DataRow**kullanarak farklı satır sürümlerine erişim hakkında bilgi için [bkz.](row-states-and-row-versions.md)</span><span class="sxs-lookup"><span data-stu-id="aeaab-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="aeaab-108">Aşağıdaki kod örneği, tablodaki tüm geçerli ve özgün değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aeaab-108">The following code example displays all the current and original values in a table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aeaab-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeaab-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="aeaab-110">DataViews</span><span class="sxs-lookup"><span data-stu-id="aeaab-110">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="aeaab-111">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aeaab-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
