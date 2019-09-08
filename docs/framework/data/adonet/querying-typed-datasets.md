---
title: Türü Belirtilmiş DataSet’leri Sorgulama
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782970"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="c918d-102">Sorgu türü belirtilmiş veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="c918d-102">Query typed DataSets</span></span>

<span data-ttu-id="c918d-103">Şeması <xref:System.Data.DataSet> uygulama tasarım zamanında biliniyorsa, LINQ to DataSet kullanırken bir tür <xref:System.Data.DataSet> kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="c918d-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="c918d-104">Türü <xref:System.Data.DataSet> , bir <xref:System.Data.DataSet>sınıfından türetilen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="c918d-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c918d-105">Bu nedenle, tüm yöntemleri, olayları ve özelliklerini <xref:System.Data.DataSet>devralır.</span><span class="sxs-lookup"><span data-stu-id="c918d-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c918d-106">Ayrıca, türü <xref:System.Data.DataSet> kesin belirlenmiş Yöntemler, olaylar ve özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c918d-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="c918d-107">Bu, koleksiyon tabanlı yöntemler kullanmak yerine tablolara ve sütunlara ada göre erişebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c918d-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="c918d-108">Bu, sorguları daha basit ve daha okunaklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c918d-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="c918d-109">Daha fazla bilgi için bkz. [türü belirtilmiş veri kümeleri](./dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="c918d-109">For more information, see [Typed DataSets](./dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="c918d-110">LINQ to DataSet, bir tür <xref:System.Data.DataSet>üzerinde sorgu yapmayı da destekler.</span><span class="sxs-lookup"><span data-stu-id="c918d-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c918d-111">Yazılı <xref:System.Data.DataSet>olarak, sütun verilerine erişmek için genel <xref:System.Data.DataRowExtensions.Field%2A> yöntemi veya <xref:System.Data.DataRowExtensions.SetField%2A> yöntemini kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c918d-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="c918d-112">Özellik adları derleme zamanında kullanılabilir, çünkü tür bilgileri içine <xref:System.Data.DataSet>dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c918d-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c918d-113">LINQ to DataSet, doğru tür olarak sütun değerlerine erişim sağlar. böylece, kod çalışma zamanı yerine kod derlendiğinde tür uyuşmazlığı hataları yakalanır.</span><span class="sxs-lookup"><span data-stu-id="c918d-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="c918d-114">Bir türü <xref:System.Data.DataSet>sorgulamaya başlayabilmeniz için, Visual Studio 'da **veri kümesi tasarımcısını** kullanarak sınıfı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c918d-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="c918d-115">Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="c918d-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="c918d-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="c918d-116">Example</span></span>

<span data-ttu-id="c918d-117">Aşağıdaki örnek, yazılı <xref:System.Data.DataSet>bir sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="c918d-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c918d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c918d-118">See also</span></span>

- [<span data-ttu-id="c918d-119">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="c918d-119">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="c918d-120">Tablolar Arası Sorgular</span><span class="sxs-lookup"><span data-stu-id="c918d-120">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="c918d-121">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="c918d-121">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
