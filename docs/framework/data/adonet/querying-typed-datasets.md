---
title: "Yazılan veri kümeleri sorgulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c232ca2888c957bea33d06c84a62b00fdc7fd80c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="querying-typed-datasets"></a><span data-ttu-id="e4fbb-102">Yazılan veri kümeleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="e4fbb-102">Querying Typed DataSets</span></span>
<span data-ttu-id="e4fbb-103">Varsa şeması <xref:System.Data.DataSet> bilinen uygulama tasarım zamanında yazılmış kullanmanızı öneririz <xref:System.Data.DataSet> kullanırken [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4fbb-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="e4fbb-104">Yazılmış bir <xref:System.Data.DataSet> türeyen bir sınıf bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e4fbb-105">Bu nedenle, tüm yöntemleri, olayları ve özelliklerini devralır bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e4fbb-106">Ayrıca, yazılı <xref:System.Data.DataSet> kesin türü belirtilmiş yöntemleri, olayları ve özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="e4fbb-107">Bu, tablolar ve sütunlar adıyla koleksiyon tabanlı yöntemleri kullanmak yerine erişebileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="e4fbb-108">Bu sorgular daha basit ve daha okunabilir yapar.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="e4fbb-109">Daha fazla bilgi için bkz: [yazılan veri kümeleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="e4fbb-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="e4fbb-110">Ayrıca yazılmış sorgulama destekler <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-110"> also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e4fbb-111">İle yazılmış bir <xref:System.Data.DataSet>, genel kullanmak zorunda değil <xref:System.Data.DataRowExtensions.Field%2A> yöntemi veya <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi sütun verilere erişme.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span>  <span data-ttu-id="e4fbb-112">Özellik adları kullanılabilir derleme zamanında tür bilgiler dahil edilir çünkü <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="e4fbb-113">böylece kodu yerine çalışma zamanında derlenen türü uyuşmazlığı hataları yakalanan sütun değerlerini erişim doğru türü olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-113"> provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>  
  
 <span data-ttu-id="e4fbb-114">Yazılmış bir sorgulama başlamadan önce <xref:System.Data.DataSet>, veri kümesi Tasarımcısı'nda kullanarak sınıfı oluşturmalıdır [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4fbb-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the DataSet Designer in [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span></span>  <span data-ttu-id="e4fbb-115">Daha fazla bilgi için bkz: [oluşturma ve veri kümelerini yapılandırma](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e4fbb-115">For more information, see [Create and configure datasets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4fbb-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4fbb-116">Example</span></span>  
 <span data-ttu-id="e4fbb-117">Aşağıdaki örnek bir sorgu yazılan gösterir <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="e4fbb-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4fbb-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4fbb-118">See Also</span></span>  
 [<span data-ttu-id="e4fbb-119">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="e4fbb-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="e4fbb-120">Tablolar Arası Sorgular</span><span class="sxs-lookup"><span data-stu-id="e4fbb-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="e4fbb-121">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="e4fbb-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
