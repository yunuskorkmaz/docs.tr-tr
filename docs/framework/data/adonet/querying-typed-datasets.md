---
title: Türü belirtilmiş DataSet'leri sorgulama
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45510006"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="867ba-102">Türü belirlenmiş veri kümelerini sorgulayın</span><span class="sxs-lookup"><span data-stu-id="867ba-102">Query typed DataSets</span></span>

<span data-ttu-id="867ba-103">Varsa şemasını <xref:System.Data.DataSet> bilinen uygulama tasarım zamanında bir türü belirtilmiş kullanmanızı öneririz <xref:System.Data.DataSet> LINQ to DataSet kullanarak.</span><span class="sxs-lookup"><span data-stu-id="867ba-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="867ba-104">Bir türü belirtilmiş <xref:System.Data.DataSet> türetildiği bir sınıf olan bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="867ba-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="867ba-105">Bu nedenle, tüm yöntemler, olaylar ve özelliklerini devralır bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="867ba-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="867ba-106">Ayrıca, belirlenmiş <xref:System.Data.DataSet> kesin türü belirtilmiş yöntemler, olaylar ve özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="867ba-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="867ba-107">Bu, tablolar ve sütunlar adıyla koleksiyon tabanlı bir yöntem kullanmak yerine erişebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="867ba-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="867ba-108">Bu sorgular daha basit ve daha okunabilir kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="867ba-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="867ba-109">Daha fazla bilgi için [yazılan veri kümeleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="867ba-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="867ba-110">LINQ to DataSet da destekler yazılmış üzerinde sorgulama <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="867ba-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="867ba-111">İle yazılmış bir <xref:System.Data.DataSet>, genel kullanmak zorunda değil <xref:System.Data.DataRowExtensions.Field%2A> yöntemi veya <xref:System.Data.DataRowExtensions.SetField%2A> sütun verilerine erişmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="867ba-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="867ba-112">Özellik adları kullanılabilir derleme zamanında tür bilgilerini bulunduğundan <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="867ba-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="867ba-113">LINQ to DataSet, sütun değerlere erişim için doğru tür olarak sağlar, böylece yerine çalışma zamanında derlenen kod türü uyuşmazlığı hatalar yakalanır.</span><span class="sxs-lookup"><span data-stu-id="867ba-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="867ba-114">Türü belirtilmiş bir sorgulama başlamadan önce <xref:System.Data.DataSet>, kullanarak bir sınıf oluşturmanız gerekir **veri kümesi Tasarımcısı** Visual Studio'da.</span><span class="sxs-lookup"><span data-stu-id="867ba-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="867ba-115">Daha fazla bilgi için [oluşturun ve veri kümeleri yapılandırma](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="867ba-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="867ba-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="867ba-116">Example</span></span>

<span data-ttu-id="867ba-117">Aşağıdaki örnek bir sorgu yazılı gösterir <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="867ba-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="867ba-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="867ba-118">See also</span></span>

- [<span data-ttu-id="867ba-119">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="867ba-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="867ba-120">Tablolar Arası Sorgular</span><span class="sxs-lookup"><span data-stu-id="867ba-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="867ba-121">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="867ba-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
