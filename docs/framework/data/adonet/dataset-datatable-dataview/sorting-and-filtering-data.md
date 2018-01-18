---
title: "Verileri sıralama ve filtreleme"
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
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2411307623c714ae521d00dcffca05d3569a656e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="b8f5a-102">Verileri sıralama ve filtreleme</span><span class="sxs-lookup"><span data-stu-id="b8f5a-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="b8f5a-103"><xref:System.Data.DataView> Sıralama ve filtreleme verileri çeşitli yollar sağlar bir <xref:System.Data.DataTable>:</span><span class="sxs-lookup"><span data-stu-id="b8f5a-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
-   <span data-ttu-id="b8f5a-104">Kullanabileceğiniz <xref:System.Data.DataView.Sort%2A> tek belirtmek için özellik veya sıralama siparişleri ve ASC (artan) ve (Azalan) DESC parametreleri dahil birden fazla sütun.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
-   <span data-ttu-id="b8f5a-105">Kullanabileceğiniz <xref:System.Data.DataView.ApplyDefaultSort%2A> artan sırada bir sıralama düzeni otomatik olarak oluşturmak için özelliğini temel tablosunun sütunlarını ve birincil anahtar sütunu üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="b8f5a-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>yalnızca aşağıdaki durumlarda uygulanır **sıralama** özelliği olan bir null başvuru ya da boş bir dize ve ne zaman tablonun tanımlı bir birincil anahtara sahip.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
-   <span data-ttu-id="b8f5a-107">Kullanabileceğiniz <xref:System.Data.DataView.RowFilter%2A> satır kümelerine belirtmek üzere özelliğe dayalı sütun değerlerine göre.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="b8f5a-108">İçin geçerli ifadeler hakkında ayrıntılı bilgi için **RowFilter** özelliği, başvuru bilgileri için bkz <xref:System.Data.DataColumn.Expression%2A> özelliği <xref:System.Data.DataColumn> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="b8f5a-109">Bir veri alt kümesini dinamik bir görünümünü sağlayarak verileri üzerinde belirli bir sorgu sonuçlarını kullanmak dönmek istiyorsanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin **DataView** en iyi performans elde etmek için yerine ayarı **RowFilter** özelliği.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="b8f5a-110">Ayarı **RowFilter** özelliği veri yükü uygulamanıza ekleme ve performans azaltmak için dizini yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="b8f5a-111">**RowFilter** özelliği en iyi kullanılır verilere bağlı uygulamada burada bağlantılı denetim filtrelenen sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="b8f5a-112">**Bul** ve **FindRows** yöntemleri yeniden oluşturulması için dizin gerek kalmadan geçerli dizini yararlanın.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="b8f5a-113">Hakkında daha fazla bilgi için **Bul** ve **FindRows** yöntemleri bkz [bulma satırları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="b8f5a-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
-   <span data-ttu-id="b8f5a-114">Kullanabileceğiniz <xref:System.Data.DataView.RowStateFilter%2A> özelliği görüntülemek için hangi satır sürümlerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="b8f5a-115">**DataView** dolaylı olarak bağlı olarak kullanıma sunmak için hangi satır sürümü yönetir **RowState** temel satır.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="b8f5a-116">Örneğin, varsa **RowStateFilter** ayarlanır **DataViewRowState.Deleted**, **DataView** sunan **özgün** satır sürümü tüm **silinmiş** olduğundan satırları hiçbir **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="b8f5a-117">Hangi satır sürümü satır kullanarak yararlanılmasını belirleyebilirsiniz **RowVersion** özelliği **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="b8f5a-118">Aşağıdaki tabloda seçeneklerini gösterir **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="b8f5a-119">DataViewRowState seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b8f5a-119">DataViewRowState options</span></span>|<span data-ttu-id="b8f5a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8f5a-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="b8f5a-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="b8f5a-121">**CurrentRows**</span></span>|<span data-ttu-id="b8f5a-122">**Geçerli** tüm satır sürümü **Unchanged**, **eklenen**, ve **değiştirilen** satır.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="b8f5a-123">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-123">This is the default.</span></span>|  
    |<span data-ttu-id="b8f5a-124">**Eklenen**</span><span class="sxs-lookup"><span data-stu-id="b8f5a-124">**Added**</span></span>|<span data-ttu-id="b8f5a-125">**Geçerli** tüm satır sürümü **eklenen** satır.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="b8f5a-126">**Deleted**</span><span class="sxs-lookup"><span data-stu-id="b8f5a-126">**Deleted**</span></span>|<span data-ttu-id="b8f5a-127">**Özgün** tüm satır sürümü **silinmiş** satır.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="b8f5a-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="b8f5a-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="b8f5a-129">**Geçerli** tüm satır sürümü **değiştirilen** satır.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="b8f5a-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="b8f5a-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="b8f5a-131">**Özgün** tüm satır sürümü **değiştirilen** satır.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="b8f5a-132">**Yok**</span><span class="sxs-lookup"><span data-stu-id="b8f5a-132">**None**</span></span>|<span data-ttu-id="b8f5a-133">Satır yok.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-133">No rows.</span></span>|  
    |<span data-ttu-id="b8f5a-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="b8f5a-134">**OriginalRows**</span></span>|<span data-ttu-id="b8f5a-135">**Özgün** tüm satır sürümü **Unchanged**, **değiştirilen**, ve **silinmiş** satır.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="b8f5a-136">**Değişmedi**</span><span class="sxs-lookup"><span data-stu-id="b8f5a-136">**Unchanged**</span></span>|<span data-ttu-id="b8f5a-137">**Geçerli** tüm satır sürümü **Unchanged** satır.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="b8f5a-138">Satır durumları ve satır sürümleri hakkında daha fazla bilgi için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b8f5a-138">For more information about row states and row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="b8f5a-139">Aşağıdaki kod örneğinde gösterildiği stoktaki birim sayısını sipariş düzeyine eşit veya daha az olduğu tüm ürünleri sıralanmış sağlayıcı kimliği ve ardından ürün adına göre ilk bir görünüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8f5a-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8f5a-140">See Also</span></span>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="b8f5a-141">DataViews</span><span class="sxs-lookup"><span data-stu-id="b8f5a-141">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="b8f5a-142">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b8f5a-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
