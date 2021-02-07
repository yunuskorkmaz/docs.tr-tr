---
description: 'Daha fazla bilgi edinin: AcceptChanges ve RejectChanges'
title: AcceptChanges ve RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: e21952063bf27f4f969669eb76b964fc7537b59a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725265"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="294ea-103">AcceptChanges ve RejectChanges</span><span class="sxs-lookup"><span data-stu-id="294ea-103">AcceptChanges and RejectChanges</span></span>

<span data-ttu-id="294ea-104">İçindeki verilerde yapılan değişikliklerin doğruluğunu doğruladıktan sonra, <xref:System.Data.DataTable> <xref:System.Data.DataRow.AcceptChanges%2A> veya, <xref:System.Data.DataRow> <xref:System.Data.DataTable> <xref:System.Data.DataSet> **geçerli** satır değerlerini **orijinal** değerler olarak ayarlanacak ve **RowState** özelliğini **değiştirilmemiş** olarak ayarlanacak olan, veya yöntemini kullanarak değişiklikleri kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="294ea-104">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="294ea-105">Değişiklikleri kabul etmek veya reddetmek, tüm **RowError** bilgilerini temizler ve **HasErrors** özelliğini **false** olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="294ea-105">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="294ea-106">Değişiklikleri kabul etme veya reddetme, veri kaynağındaki verileri güncelleştirmeyi de etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="294ea-106">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="294ea-107">Daha fazla bilgi için bkz. [veri kaynaklarını DataAdapter Ile güncelleştirme](../updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="294ea-107">For more information, see [Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="294ea-108">**DataTable** üzerinde yabancı anahtar kısıtlamaları varsa, **AcceptChanges** ve **RejectChanges** kullanılarak kabul edilen veya reddedilen değişiklikler, **ForeignKeyConstraint. AcceptRejectRule** öğesine göre **DataRow** 'ın alt satırlarına yayılır.</span><span class="sxs-lookup"><span data-stu-id="294ea-108">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="294ea-109">Daha fazla bilgi için bkz. [DataTable kısıtlamaları](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="294ea-109">For more information, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="294ea-110">Aşağıdaki örnek, hataları olan satırları denetler, uygun olduğunda hataları çözer ve hatanın çözümlenemediği satırları reddeder.</span><span class="sxs-lookup"><span data-stu-id="294ea-110">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="294ea-111">Çözümlenen hatalar için **RowError** değeri ' nin boş bir dizeye sıfırlandığını ve **HasErrors** özelliğinin **false** olarak ayarlanmasına neden olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="294ea-111">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="294ea-112">Hata içeren tüm satırlar çözümlendiğinde veya reddedildiğinde, **AcceptChanges** tüm **DataTable** için tüm değişiklikleri kabul etmek üzere çağırılır.</span><span class="sxs-lookup"><span data-stu-id="294ea-112">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="294ea-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="294ea-113">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="294ea-114">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="294ea-114">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="294ea-115">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="294ea-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
