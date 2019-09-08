---
title: DataRows ve DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 7c76435b8a0f7a874504813d91d5eda929d08f67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786428"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="16c16-102">DataRows ve DataRowViews</span><span class="sxs-lookup"><span data-stu-id="16c16-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="16c16-103"><xref:System.Data.DataView> ,<xref:System.Data.DataRowView> Nesnelerin sıralanabilir koleksiyonunu ortaya koyar.</span><span class="sxs-lookup"><span data-stu-id="16c16-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="16c16-104">**DataRowView** nesneleri değerleri, temel tablodaki sütunun adı ya da Ordinal başvurusu tarafından dizine alınmış nesne dizileri olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="16c16-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="16c16-105">DataRowView 'ın <xref:System.Data.DataRowView.Row%2A> özelliğini kullanarak <xref:System.Data.DataRow> **DataRowView** tarafından açığa çıkarılan öğesine **erişebilirsiniz.**</span><span class="sxs-lookup"><span data-stu-id="16c16-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="16c16-106">Bir **DataRowView**kullanarak değerleri görüntülediğinizde, <xref:System.Data.DataView.RowStateFilter%2A> **DataView** özelliği temel alınan **DataRow** 'ın hangi satır sürümünün açığa çıkardığını belirler.</span><span class="sxs-lookup"><span data-stu-id="16c16-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="16c16-107">Bir **DataRow**kullanarak farklı satır sürümlerine erişme hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="16c16-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="16c16-108">Aşağıdaki kod örneği, bir tablodaki tüm geçerli ve orijinal değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="16c16-108">The following code example displays all the current and original values in a table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16c16-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16c16-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="16c16-110">DataViews</span><span class="sxs-lookup"><span data-stu-id="16c16-110">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="16c16-111">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="16c16-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
