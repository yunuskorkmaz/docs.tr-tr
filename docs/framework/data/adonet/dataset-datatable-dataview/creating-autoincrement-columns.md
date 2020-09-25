---
title: AutoIncrement Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 9a979f39003e60c70c03206bd886bdd6827c82e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203728"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="d377c-102">AutoIncrement Sütunları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d377c-102">Creating AutoIncrement Columns</span></span>

<span data-ttu-id="d377c-103">Benzersiz sütun değerlerini sağlamak için, tabloya yeni satırlar eklendiğinde sütun değerlerini otomatik olarak artır olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d377c-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="d377c-104">Otomatik artırma oluşturmak için <xref:System.Data.DataColumn> <xref:System.Data.DataColumn.AutoIncrement%2A> sütunun özelliğini **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d377c-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="d377c-105"><xref:System.Data.DataColumn>Sonra, özelliğinde tanımlanan değerle başlar <xref:System.Data.DataColumn.AutoIncrementSeed%2A> ve her satır, **AutoIncrement** sütununun değeri sütunun özelliğinde tanımlanan değere göre artar <xref:System.Data.DataColumn.AutoIncrementStep%2A> .</span><span class="sxs-lookup"><span data-stu-id="d377c-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="d377c-106">**AutoIncrement** sütunları Için, <xref:System.Data.DataColumn.ReadOnly%2A> **DataColumn** özelliğinin özelliğinin **true**olarak ayarlanması önerilir.</span><span class="sxs-lookup"><span data-stu-id="d377c-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="d377c-107">Aşağıdaki örnek, 200 değeriyle başlayan ve adım adım 3 ' ü ekleyen bir sütunun nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d377c-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="d377c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d377c-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="d377c-109">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="d377c-109">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="d377c-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="d377c-110">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="d377c-111">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d377c-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
