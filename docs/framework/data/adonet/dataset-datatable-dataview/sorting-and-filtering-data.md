---
description: 'Daha fazla bilgi edinin: verileri sıralama ve filtreleme'
title: Verileri Sıralama ve Filtreleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: a8b74dc13e88f8d5e70bb27291e0e6e34817f0ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651619"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="fde46-103">Verileri Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="fde46-103">Sorting and Filtering Data</span></span>

<span data-ttu-id="fde46-104">, <xref:System.Data.DataView> Bir içindeki verileri sıralamak ve filtrelemek için çeşitli yollar sağlar <xref:System.Data.DataTable> :</span><span class="sxs-lookup"><span data-stu-id="fde46-104">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
- <span data-ttu-id="fde46-105"><xref:System.Data.DataView.Sort%2A>Özelliğini kullanarak tek veya birden çok sütun sıralama düzeni belirtebilir ve ASC (artan) ve DESC (azalan) parametreleri dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fde46-105">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
- <span data-ttu-id="fde46-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>Özelliğini, tablonun birincil anahtar sütununa veya sütunlarına göre artan sırada otomatik olarak bir sıralama düzeni oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fde46-106">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="fde46-107"><xref:System.Data.DataView.ApplyDefaultSort%2A> yalnızca **sıralama** özelliği null veya boş bir dize olduğunda ve tablonun tanımlı bir birincil anahtarı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fde46-107"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
- <span data-ttu-id="fde46-108"><xref:System.Data.DataView.RowFilter%2A>Özelliğini, sütun değerlerine göre satır alt kümelerini belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fde46-108">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="fde46-109">**RowFilter** özelliği için geçerli ifadeler hakkında daha fazla bilgi için, sınıfının özelliği için başvuru bilgilerine bakın <xref:System.Data.DataColumn.Expression%2A> <xref:System.Data.DataColumn> .</span><span class="sxs-lookup"><span data-stu-id="fde46-109">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="fde46-110">Verilerin bir alt kümesinin dinamik görünümünü sağlamanın aksine veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> **RowFilter** özelliğini ayarlamak yerine en iyi performansı elde etmek için **DataView** 'ın veya yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fde46-110">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="fde46-111">**RowFilter** özelliğinin ayarlanması, verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır.</span><span class="sxs-lookup"><span data-stu-id="fde46-111">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="fde46-112">**RowFilter** özelliği, bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fde46-112">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="fde46-113">**Find** ve **FindRows** yöntemleri, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="fde46-113">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="fde46-114">**Find** ve **FindRows** yöntemleri hakkında daha fazla bilgi Için bkz. [satırları bulma](finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="fde46-114">For more information about the **Find** and **FindRows** methods, see [Finding Rows](finding-rows.md).</span></span>  
  
- <span data-ttu-id="fde46-115"><xref:System.Data.DataView.RowStateFilter%2A>Hangi satır sürümlerinin görüntüleneceği belirlemek için özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fde46-115">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="fde46-116">**DataView** , temel alınan satırın **RowState** öğesine bağlı olarak hangi satır sürümünün sergileceğini dolaylı olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="fde46-116">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="fde46-117">Örneğin, **RowStateFilter** , **DataViewRowState. Deleted** olarak ayarlandıysa, **geçerli** satır sürümü bulunmadığından **DataView** , **silinen** tüm satırların **orijinal** satır sürümünü kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="fde46-117">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="fde46-118">**DataRowView**'ın **ROWVERSION** özelliğini kullanarak bir satırın hangi satır sürümünün gösterilmesini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fde46-118">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="fde46-119">Aşağıdaki tabloda, **DataViewRowState** seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fde46-119">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="fde46-120">DataViewRowState seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fde46-120">DataViewRowState options</span></span>|<span data-ttu-id="fde46-121">Description</span><span class="sxs-lookup"><span data-stu-id="fde46-121">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="fde46-122">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="fde46-122">**CurrentRows**</span></span>|<span data-ttu-id="fde46-123">Tüm **değişmemiş**, **eklenen** ve **değiştirilen** satırların **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="fde46-123">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="fde46-124">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="fde46-124">This is the default.</span></span>|  
    |<span data-ttu-id="fde46-125">**Eklenirse**</span><span class="sxs-lookup"><span data-stu-id="fde46-125">**Added**</span></span>|<span data-ttu-id="fde46-126">Tüm **eklenen** satırların **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="fde46-126">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="fde46-127">**Silindi**</span><span class="sxs-lookup"><span data-stu-id="fde46-127">**Deleted**</span></span>|<span data-ttu-id="fde46-128">**Silinen** tüm satırların **orijinal** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="fde46-128">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="fde46-129">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="fde46-129">**ModifiedCurrent**</span></span>|<span data-ttu-id="fde46-130">**Değiştirilen** tüm satırların **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="fde46-130">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="fde46-131">**Modifiedorijinal**</span><span class="sxs-lookup"><span data-stu-id="fde46-131">**ModifiedOriginal**</span></span>|<span data-ttu-id="fde46-132">**Değiştirilen** tüm satırların **orijinal** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="fde46-132">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="fde46-133">**Hiçbiri**</span><span class="sxs-lookup"><span data-stu-id="fde46-133">**None**</span></span>|<span data-ttu-id="fde46-134">Satır yok.</span><span class="sxs-lookup"><span data-stu-id="fde46-134">No rows.</span></span>|  
    |<span data-ttu-id="fde46-135">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="fde46-135">**OriginalRows**</span></span>|<span data-ttu-id="fde46-136">Tüm **değişmemiş**, **değiştirilen** ve **silinen** satırların **orijinal** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="fde46-136">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="fde46-137">**Değiştirilmediği**</span><span class="sxs-lookup"><span data-stu-id="fde46-137">**Unchanged**</span></span>|<span data-ttu-id="fde46-138">**Değişmeyen** tüm satırların **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="fde46-138">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="fde46-139">Satır durumları ve satır sürümleri hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="fde46-139">For more information about row states and row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="fde46-140">Aşağıdaki kod örneği, stoktaki birim sayısının yeniden sipariş düzeyine eşit veya daha küçük olduğu, önce Tedarikçi KIMLIĞI ve ardından ürün adına göre sıralanmış tüm ürünleri gösteren bir görünüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fde46-140">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fde46-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fde46-141">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="fde46-142">DataViews</span><span class="sxs-lookup"><span data-stu-id="fde46-142">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="fde46-143">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fde46-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
