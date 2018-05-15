---
title: AcceptChanges ve RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: 65e47bafda3e3e47241405c9c8b8e3b4b0055601
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="9c479-102">AcceptChanges ve RejectChanges</span><span class="sxs-lookup"><span data-stu-id="9c479-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="9c479-103">Verilerde yapılan değişiklikleri doğruluğunu doğruladıktan sonra bir <xref:System.Data.DataTable>, kullanarak değişikliği kabul edebilen <xref:System.Data.DataRow.AcceptChanges%2A> yöntemi <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataSet>, hangi ayarlayacak **geçerli** satır değerleri **özgün** değerleri ve ayarlar **RowState** özelliğine **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="9c479-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="9c479-104">Değişiklikleri kabul veya reddetmek temizler herhangi **RowError** bilgi ve kümelerini **HasErrors** özelliğine **false**.</span><span class="sxs-lookup"><span data-stu-id="9c479-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="9c479-105">Ayrıca veri kaynağındaki güncelleştirme veri değişiklikleri kabul veya reddetmek etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="9c479-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="9c479-106">Daha fazla bilgi için bkz: [veri kaynaklarıyla güncelleştirme DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="9c479-106">For more information, see [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="9c479-107">Yabancı anahtar kısıtlamaları üzerinde varsa **DataTable**, değişiklikleri kabul veya kullanarak **AcceptChanges** ve **RejectChanges** altsatırlarınayayılır **DataRow** göre **ForeignKeyConstraint.AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="9c479-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="9c479-108">Daha fazla bilgi için bkz: [DataTable kısıtlamalarını](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="9c479-108">For more information, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="9c479-109">Aşağıdaki örnek, hatalarla satırları denetler uygunsa hataları giderir ve burada hata çözümlenemiyor satırları reddeder.</span><span class="sxs-lookup"><span data-stu-id="9c479-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="9c479-110">Hatalar için çözümlenen Not **RowError** değeri, boş bir dize olarak sıfırlanır neden **HasErrors** ayarlamak için özellik **false**.</span><span class="sxs-lookup"><span data-stu-id="9c479-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="9c479-111">Hataları olan tüm satırları çözülmüş veya reddedilen **AcceptChanges** tüm için tüm değişiklikleri kabul etmek için çağrılan **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="9c479-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c479-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c479-112">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="9c479-113">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="9c479-113">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="9c479-114">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9c479-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
