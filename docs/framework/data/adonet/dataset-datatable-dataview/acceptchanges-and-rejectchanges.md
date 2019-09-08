---
title: AcceptChanges ve RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: c537fa808fc6ba4c740e71bfd70fe9cd1f3bd31a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785567"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="c375e-102">AcceptChanges ve RejectChanges</span><span class="sxs-lookup"><span data-stu-id="c375e-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="c375e-103"><xref:System.Data.DataTable>Bir içindeki verilerde yapılan değişikliklerin doğruluğunu doğruladıktan sonra,, veya, **geçerli** satır değerlerini şu şekilde ayarlanacak şekilde <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow> <xref:System.Data.DataTable> <xref:System.Data.DataSet> **,, veya yöntemini kullanarak değişiklikleri kabul edebilirsiniz. Özgün** değerler ve **RowState** özelliğini **Unchanged**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c375e-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="c375e-104">Değişiklikleri kabul etmek veya reddetmek, tüm **RowError** bilgilerini temizler ve **HasErrors** özelliğini **false**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c375e-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="c375e-105">Değişiklikleri kabul etme veya reddetme, veri kaynağındaki verileri güncelleştirmeyi de etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="c375e-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="c375e-106">Daha fazla bilgi için bkz. [veri kaynaklarını DataAdapter Ile güncelleştirme](../updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="c375e-106">For more information, see [Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="c375e-107">**DataTable**üzerinde yabancı anahtar kısıtlamaları varsa, **AcceptChanges** ve **RejectChanges** kullanılarak kabul edilen veya reddedilen değişiklikler **DataRow** öğesinin alt satırlarına göre  **ForeignKeyConstraint. AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="c375e-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="c375e-108">Daha fazla bilgi için bkz. [DataTable kısıtlamaları](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="c375e-108">For more information, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="c375e-109">Aşağıdaki örnek, hataları olan satırları denetler, uygun olduğunda hataları çözer ve hatanın çözümlenemediği satırları reddeder.</span><span class="sxs-lookup"><span data-stu-id="c375e-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="c375e-110">Çözümlenen hatalar için **RowError** değeri ' nin boş bir dizeye sıfırlandığını ve **HasErrors** özelliğinin **false**olarak ayarlanmasına neden olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c375e-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="c375e-111">Hata içeren tüm satırlar çözümlendiğinde veya reddedildiğinde, **AcceptChanges** tüm **DataTable**için tüm değişiklikleri kabul etmek üzere çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c375e-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a><span data-ttu-id="c375e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c375e-112">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="c375e-113">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="c375e-113">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="c375e-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c375e-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
