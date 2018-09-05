---
title: Verileri sıralama ve filtreleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: ade08deca909b32090b7d2d7cf8c6ba9ce9e7679
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538689"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="a501c-102">Verileri sıralama ve filtreleme</span><span class="sxs-lookup"><span data-stu-id="a501c-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="a501c-103"><xref:System.Data.DataView> İçindeki verileri sıralama ve filtreleme çeşitli yollarını sağlar bir <xref:System.Data.DataTable>:</span><span class="sxs-lookup"><span data-stu-id="a501c-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
-   <span data-ttu-id="a501c-104">Kullanabileceğiniz <xref:System.Data.DataView.Sort%2A> tek belirtmek için özelliği veya sıralama düzenlerine ve ASC (artan) ve (Azalan) DESC parametreleri içeren birden çok sütunu.</span><span class="sxs-lookup"><span data-stu-id="a501c-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
-   <span data-ttu-id="a501c-105">Kullanabileceğiniz <xref:System.Data.DataView.ApplyDefaultSort%2A> özelliği otomatik olarak bir sıralama düzeni artan düzende oluşturmak için temel tablonun sütunlarının ve birincil anahtar sütunu üzerinde.</span><span class="sxs-lookup"><span data-stu-id="a501c-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="a501c-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> yalnızca geçerli **sıralama** özelliği null bir başvuru ya da boş bir dize ve tabloda bir birincil anahtar tanımlı olduğunda.</span><span class="sxs-lookup"><span data-stu-id="a501c-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
-   <span data-ttu-id="a501c-107">Kullanabileceğiniz <xref:System.Data.DataView.RowFilter%2A> satır kümelerine belirtmek için özellik sütun değerlerine bağlı.</span><span class="sxs-lookup"><span data-stu-id="a501c-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="a501c-108">İçin geçerli ifadeler hakkında daha fazla ayrıntı için **RowFilter** özelliğine başvuru bilgilerine bakın <xref:System.Data.DataColumn.Expression%2A> özelliği <xref:System.Data.DataColumn> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a501c-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="a501c-109">Verilerin bir alt kümesini, dinamik bir görünüm sağlayarak veriler üzerinde belirli bir sorgu sonuçlarını kullanma dönmek istiyorsanız <xref:System.Data.DataView.Find%2A> veya <xref:System.Data.DataView.FindRows%2A> yöntemlerinin **DataView** en iyi performans elde etmek için değil ayarı **RowFilter** özelliği.</span><span class="sxs-lookup"><span data-stu-id="a501c-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="a501c-110">Ayarı **RowFilter** özelliği yükü uygulamanıza ekleme ve performansı azaltarak veri dizini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a501c-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="a501c-111">**RowFilter** özelliği en iyi şekilde kullanılır verilere bağlı uygulamada nereye bağlantılı denetim filtrelenmiş sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a501c-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="a501c-112">**Bul** ve **FindRows** yöntemleri, yeniden oluşturulması için dizini gerek kalmadan geçerli dizini yararlanın.</span><span class="sxs-lookup"><span data-stu-id="a501c-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="a501c-113">Hakkında daha fazla bilgi için **Bul** ve **FindRows** yöntemleri bkz [satırları bulma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="a501c-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
-   <span data-ttu-id="a501c-114">Kullanabileceğiniz <xref:System.Data.DataView.RowStateFilter%2A> özelliği görüntülemek için hangi satır sürümleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="a501c-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="a501c-115">**DataView** örtük olarak bağlı olarak kullanıma sunmak için hangi satır sürümünü yönetir **RowState** temel alınan satır.</span><span class="sxs-lookup"><span data-stu-id="a501c-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="a501c-116">Örneğin, varsa **RowStateFilter** ayarlanır **DataViewRowState.Deleted**, **DataView** sunan **özgün** satır sürümü tüm **silinmiş** olduğundan satırları hiçbir **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="a501c-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="a501c-117">Satır hangi satır sürümünü kullanarak açıklanmasını belirlemek **RowVersion** özelliği **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="a501c-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="a501c-118">Aşağıdaki tabloda ilişkin seçenekler gösterilir **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="a501c-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="a501c-119">DataViewRowState seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a501c-119">DataViewRowState options</span></span>|<span data-ttu-id="a501c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a501c-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="a501c-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="a501c-121">**CurrentRows**</span></span>|<span data-ttu-id="a501c-122">**Geçerli** satır sürümü tüm **Unchanged**, **eklenen**, ve **değiştirilen** satır.</span><span class="sxs-lookup"><span data-stu-id="a501c-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="a501c-123">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a501c-123">This is the default.</span></span>|  
    |<span data-ttu-id="a501c-124">**Eklendi**</span><span class="sxs-lookup"><span data-stu-id="a501c-124">**Added**</span></span>|<span data-ttu-id="a501c-125">**Geçerli** satır sürümü tüm **eklenen** satır.</span><span class="sxs-lookup"><span data-stu-id="a501c-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="a501c-126">**silindi**</span><span class="sxs-lookup"><span data-stu-id="a501c-126">**Deleted**</span></span>|<span data-ttu-id="a501c-127">**Özgün** satır sürümü tüm **silinmiş** satır.</span><span class="sxs-lookup"><span data-stu-id="a501c-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="a501c-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="a501c-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="a501c-129">**Geçerli** satır sürümü tüm **değiştirilen** satır.</span><span class="sxs-lookup"><span data-stu-id="a501c-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="a501c-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="a501c-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="a501c-131">**Özgün** satır sürümü tüm **değiştirilen** satır.</span><span class="sxs-lookup"><span data-stu-id="a501c-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="a501c-132">**Yok**</span><span class="sxs-lookup"><span data-stu-id="a501c-132">**None**</span></span>|<span data-ttu-id="a501c-133">Satır yok.</span><span class="sxs-lookup"><span data-stu-id="a501c-133">No rows.</span></span>|  
    |<span data-ttu-id="a501c-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="a501c-134">**OriginalRows**</span></span>|<span data-ttu-id="a501c-135">**Özgün** satır sürümü tüm **Unchanged**, **değiştirilen**, ve **silinmiş** satır.</span><span class="sxs-lookup"><span data-stu-id="a501c-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="a501c-136">**değişmedi**</span><span class="sxs-lookup"><span data-stu-id="a501c-136">**Unchanged**</span></span>|<span data-ttu-id="a501c-137">**Geçerli** satır sürümü tüm **Unchanged** satır.</span><span class="sxs-lookup"><span data-stu-id="a501c-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="a501c-138">Satır durumları ve satır sürümleri hakkında daha fazla bilgi için bkz. [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="a501c-138">For more information about row states and row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="a501c-139">Aşağıdaki kod örneği, stoktaki birim sayısını ya da yeniden sıralama düzeyi eşit olduğu tüm ürünleri gösterir sıralanmış sağlayıcı kimliği ve ardından ürün adına göre öncelikle bir görünüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a501c-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a501c-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a501c-140">See Also</span></span>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="a501c-141">DataViews</span><span class="sxs-lookup"><span data-stu-id="a501c-141">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="a501c-142">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a501c-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
