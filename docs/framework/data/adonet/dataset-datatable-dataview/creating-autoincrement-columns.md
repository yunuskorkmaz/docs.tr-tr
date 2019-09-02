---
title: AutoIncrement Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 2548ad9382b406978dac0a3d366207626278f501
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205136"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="09a02-102">AutoIncrement Sütunları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="09a02-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="09a02-103">Benzersiz sütun değerlerini sağlamak için, tabloya yeni satırlar eklendiğinde sütun değerlerini otomatik olarak artır olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09a02-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="09a02-104">Otomatik artırma <xref:System.Data.DataColumn>oluşturmak için sütunun <xref:System.Data.DataColumn.AutoIncrement%2A> özelliğini **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="09a02-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="09a02-105">Sonra, <xref:System.Data.DataColumn.AutoIncrementSeed%2A> özelliğinde tanımlanan değerle başlar ve her satır, **AutoIncrement** sütununun değeri sütunun <xref:System.Data.DataColumn.AutoIncrementStep%2A> özelliğinde tanımlanan değere göre artar. <xref:System.Data.DataColumn></span><span class="sxs-lookup"><span data-stu-id="09a02-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="09a02-106">**AutoIncrement** sütunları için, <xref:System.Data.DataColumn.ReadOnly%2A> **DataColumn** özelliğinin özelliğinin **true**olarak ayarlanması önerilir.</span><span class="sxs-lookup"><span data-stu-id="09a02-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="09a02-107">Aşağıdaki örnek, 200 değeriyle başlayan ve adım adım 3 ' ü ekleyen bir sütunun nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="09a02-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09a02-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09a02-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="09a02-109">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="09a02-109">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="09a02-110">DataTables</span><span class="sxs-lookup"><span data-stu-id="09a02-110">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="09a02-111">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="09a02-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
