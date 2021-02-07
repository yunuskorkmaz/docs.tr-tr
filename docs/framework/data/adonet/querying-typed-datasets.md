---
description: 'Hakkında daha fazla bilgi edinin: sorgu türü belirtilmiş veri kümeleri'
title: Türü Belirtilmiş DataSet’leri Sorgulama
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 5bcf8bb587a0ed0eaca1bbe9b3a7d7143757780e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723705"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="397f3-103">Sorgu türü belirtilmiş veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="397f3-103">Query typed DataSets</span></span>

<span data-ttu-id="397f3-104">Şeması <xref:System.Data.DataSet> uygulama tasarım zamanında biliniyorsa, LINQ to DataSet kullanırken bir tür kullanmanızı öneririz <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="397f3-104">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="397f3-105">Türü <xref:System.Data.DataSet> , bir sınıfından türetilen bir sınıftır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="397f3-105">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="397f3-106">Bu nedenle, tüm yöntemleri, olayları ve özelliklerini devralır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="397f3-106">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="397f3-107">Ayrıca, türü <xref:System.Data.DataSet> kesin belirlenmiş Yöntemler, olaylar ve özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="397f3-107">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="397f3-108">Bu, koleksiyon tabanlı yöntemler kullanmak yerine tablolara ve sütunlara ada göre erişebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="397f3-108">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="397f3-109">Bu, sorguları daha basit ve daha okunaklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="397f3-109">This makes queries simpler and more readable.</span></span> <span data-ttu-id="397f3-110">Daha fazla bilgi için bkz. [türü belirtilmiş veri kümeleri](./dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="397f3-110">For more information, see [Typed DataSets](./dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="397f3-111">LINQ to DataSet, bir tür üzerinde sorgu yapmayı da destekler <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="397f3-111">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="397f3-112">Yazılı <xref:System.Data.DataSet> olarak, <xref:System.Data.DataRowExtensions.Field%2A> <xref:System.Data.DataRowExtensions.SetField%2A> sütun verilerine erişmek için genel yöntemi veya yöntemini kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="397f3-112">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="397f3-113">Özellik adları derleme zamanında kullanılabilir, çünkü tür bilgileri içine dahil edilmiştir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="397f3-113">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="397f3-114">LINQ to DataSet, doğru tür olarak sütun değerlerine erişim sağlar. böylece, kod çalışma zamanı yerine kod derlendiğinde tür uyuşmazlığı hataları yakalanır.</span><span class="sxs-lookup"><span data-stu-id="397f3-114">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="397f3-115">Bir türü sorgulamaya başlayabilmeniz için <xref:System.Data.DataSet> , Visual Studio 'Da **veri kümesi tasarımcısını** kullanarak sınıfı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="397f3-115">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="397f3-116">Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="397f3-116">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="397f3-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="397f3-117">Example</span></span>

<span data-ttu-id="397f3-118">Aşağıdaki örnek, yazılı bir sorgu gösterir <xref:System.Data.DataSet> :</span><span class="sxs-lookup"><span data-stu-id="397f3-118">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a><span data-ttu-id="397f3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="397f3-119">See also</span></span>

- [<span data-ttu-id="397f3-120">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="397f3-120">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="397f3-121">Tablolar Arası Sorgular</span><span class="sxs-lookup"><span data-stu-id="397f3-121">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="397f3-122">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="397f3-122">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
