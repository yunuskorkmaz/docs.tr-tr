---
title: DataView ile sıralama (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: d80c00a4b06a31f61a521e7206c204c02106748a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175284"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a><span data-ttu-id="e67c0-102">DataView ile sıralama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e67c0-102">Sorting with DataView (LINQ to DataSet)</span></span>

<span data-ttu-id="e67c0-103">Verileri belirli ölçütlere göre sıralama ve sonra verileri bir kullanıcı arabirimi denetimi aracılığıyla bir istemciye sunma özelliği, veri bağlamanın önemli bir yönüdür.</span><span class="sxs-lookup"><span data-stu-id="e67c0-103">The ability to sort data based on specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="e67c0-104"><xref:System.Data.DataView> verileri sıralamak ve belirli sıralama ölçütlerine göre sıralanmış veri satırlarını döndürmek için çeşitli yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e67c0-104"><xref:System.Data.DataView> provides several ways to sort data and return data rows ordered by specific ordering criteria.</span></span> <span data-ttu-id="e67c0-105">Dize tabanlı sıralama yeteneklerine ek olarak, <xref:System.Data.DataView> Sıralama ölçütleri Için dil Ile tümleşik sorgu (LINQ) ifadelerini de kullanmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="e67c0-105">In addition to its string-based sorting capabilities, <xref:System.Data.DataView> also enables you to use Language-Integrated Query (LINQ) expressions for the sorting criteria.</span></span> <span data-ttu-id="e67c0-106">LINQ ifadeleri, dize tabanlı sıralamaya kıyasla çok daha karmaşık ve güçlü sıralama işlemlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e67c0-106">LINQ expressions allow for much more complex and powerful sorting operations than string-based sorting.</span></span> <span data-ttu-id="e67c0-107">Bu konuda, kullanarak sıralama için her iki yaklaşım da açıklanmaktadır <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="e67c0-107">This topic describes both approaches to sorting using <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a><span data-ttu-id="e67c0-108">Sıralama bilgileriyle bir sorgudan DataView oluşturma</span><span class="sxs-lookup"><span data-stu-id="e67c0-108">Creating DataView from a Query with Sorting Information</span></span>  

 <span data-ttu-id="e67c0-109">Bir <xref:System.Data.DataView> nesne, bir LINQ to DataSet sorgusundan oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="e67c0-109">A <xref:System.Data.DataView> object can be created from a LINQ to DataSet query.</span></span> <span data-ttu-id="e67c0-110">Bu sorgu bir,, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> <xref:System.Linq.Enumerable.ThenBy%2A> veya <xref:System.Linq.Enumerable.ThenByDescending%2A> yan tümce içeriyorsa, bu yan tümcelerdeki ifadeler, içindeki verileri sıralamaya yönelik temel olarak kullanılır <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="e67c0-110">If that query contains an <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, or <xref:System.Linq.Enumerable.ThenByDescending%2A> clause the expressions in these clauses are used as the basis for sorting the data in the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="e67c0-111">Örneğin, sorgu `Order By…` ve `Then By…` yan tümceleri içeriyorsa, sonuçta <xref:System.Data.DataView> verileri belirtilen her iki sütuna göre sıraya alır.</span><span class="sxs-lookup"><span data-stu-id="e67c0-111">For example, if the query contains the `Order By…`and `Then By…` clauses, the resulting <xref:System.Data.DataView> would order the data by both columns specified.</span></span>  
  
 <span data-ttu-id="e67c0-112">İfade tabanlı sıralama, daha basit dize tabanlı sıralamaya kıyasla daha güçlü ve karmaşık sıralama sağlar.</span><span class="sxs-lookup"><span data-stu-id="e67c0-112">Expression-based sorting offers more powerful and complex sorting than the simpler string-based sorting.</span></span> <span data-ttu-id="e67c0-113">Dize tabanlı ve ifade tabanlı sıralamanın birbirini dışlamadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e67c0-113">Note that string-based and expression-based sorting are mutually exclusive.</span></span> <span data-ttu-id="e67c0-114">Dize tabanlı, bir <xref:System.Data.DataView.Sort%2A> sorgudan oluşturulduktan sonra ayarlandıysa <xref:System.Data.DataView> , sorgudan çıkarılan ifade tabanlı filtre temizlenir ve sıfırlanamaz.</span><span class="sxs-lookup"><span data-stu-id="e67c0-114">If the string-based <xref:System.Data.DataView.Sort%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression-based filter inferred from the query is cleared and cannot be reset.</span></span>  
  
 <span data-ttu-id="e67c0-115">' A ait dizin, <xref:System.Data.DataView> her ikisi de <xref:System.Data.DataView> oluşturulduğunda ve sıralama ya da filtreleme bilgisi değiştirildiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e67c0-115">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="e67c0-116">Tarafından oluşturulan LINQ to DataSet sorgusunda sıralama ölçütlerini sağlayarak en iyi performansı elde edersiniz <xref:System.Data.DataView> ve sıralama bilgilerini daha sonra değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="e67c0-116">You get the best performance by supplying sorting criteria in the LINQ to DataSet query that the <xref:System.Data.DataView> is created from and not modifying the sorting information, later.</span></span> <span data-ttu-id="e67c0-117">Daha fazla bilgi için bkz. [DataView performansı](dataview-performance.md).</span><span class="sxs-lookup"><span data-stu-id="e67c0-117">For more information, see [DataView Performance](dataview-performance.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e67c0-118">Çoğu durumda, sıralama için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e67c0-118">In most cases, the expressions used for sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="e67c0-119">Ayrıca, sıralama işlemleri herhangi bir sayıda yürütülene kadar, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="e67c0-119">Also, the expressions should not contain any logic that depends on a set number of executions, because the sorting operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e67c0-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="e67c0-120">Example</span></span>  

 <span data-ttu-id="e67c0-121">Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırları sipariş tarihine göre sıralar; <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' <xref:System.Data.DataView> a bağlar <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="e67c0-121">The following example queries the SalesOrderHeader table and orders the returned rows by the order date; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a><span data-ttu-id="e67c0-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="e67c0-122">Example</span></span>  

 <span data-ttu-id="e67c0-123">Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırı toplam tutara göre sıralar; <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' <xref:System.Data.DataView> a bağlar <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="e67c0-123">The following example queries the SalesOrderHeader table and orders the returned row by total amount due; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a><span data-ttu-id="e67c0-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e67c0-124">Example</span></span>  

 <span data-ttu-id="e67c0-125">Aşağıdaki örnek, SalesOrderDetail tablosunu sorgular ve döndürülen satırları sipariş miktarına göre ve satış siparişi koduna göre sıralar; <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' <xref:System.Data.DataView> a bağlar <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="e67c0-125">The following example queries the SalesOrderDetail table and orders the returned rows by order quantity and then by sales order ID; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a><span data-ttu-id="e67c0-126">Dize tabanlı sıralama özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="e67c0-126">Using the String-Based Sort Property</span></span>  

 <span data-ttu-id="e67c0-127">Dize tabanlı sıralama işlevselliği <xref:System.Data.DataView> LINQ to DataSet ile hala işe yarar.</span><span class="sxs-lookup"><span data-stu-id="e67c0-127">The string-based sorting functionality of <xref:System.Data.DataView> still works with LINQ to DataSet.</span></span> <span data-ttu-id="e67c0-128">Bir LINQ to DataSet sorgusundan oluşturulduktan sonra, <xref:System.Data.DataView> <xref:System.Data.DataView.Sort%2A> üzerinde sıralamayı ayarlamak için özelliğini kullanabilirsiniz <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="e67c0-128">After a <xref:System.Data.DataView> has been created from a LINQ to DataSet query, you can use the <xref:System.Data.DataView.Sort%2A> property to set the sorting on the <xref:System.Data.DataView>.</span></span>  
  
 <span data-ttu-id="e67c0-129">Dize tabanlı ve ifade tabanlı sıralama işlevselliği birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="e67c0-129">The string-based and expression-based sorting functionality are mutually exclusive.</span></span> <span data-ttu-id="e67c0-130">Özelliği ayarlandığında <xref:System.Data.DataView.Sort%2A> , tarafından oluşturulan sorgudan devralınan ifade tabanlı sıralama temizlenir <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="e67c0-130">Setting the <xref:System.Data.DataView.Sort%2A> property will clear the expression-based sort inherited from the query that the <xref:System.Data.DataView> was created from.</span></span>  
  
 <span data-ttu-id="e67c0-131">Dize tabanlı filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView.Sort%2A> bkz. [verileri sıralama ve filtreleme](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="e67c0-131">For more information about string-based <xref:System.Data.DataView.Sort%2A> filtering, see [Sorting and Filtering Data](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="e67c0-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="e67c0-132">Example</span></span>  

 <span data-ttu-id="e67c0-133">Takip eden örnek, <xref:System.Data.DataView> kişi tablosundan bir oluşturur ve satırları son ada göre azalan düzende sıralar, ardından ilk adı artan sırada yapar:</span><span class="sxs-lookup"><span data-stu-id="e67c0-133">The follow example creates a <xref:System.Data.DataView> from the Contact table and sorts the rows by last name in descending order, then first name in ascending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a><span data-ttu-id="e67c0-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="e67c0-134">Example</span></span>  

 <span data-ttu-id="e67c0-135">Aşağıdaki örnek, "S" harfiyle başlayan son adlarla Ilgili kişi tablosunu sorgular.</span><span class="sxs-lookup"><span data-stu-id="e67c0-135">The following example queries the Contact table for last names that start with the letter "S".</span></span>  <span data-ttu-id="e67c0-136"><xref:System.Data.DataView>Bu sorgudan oluşturulur ve bir <xref:System.Windows.Forms.BindingSource> nesneye bağlanır.</span><span class="sxs-lookup"><span data-stu-id="e67c0-136">A <xref:System.Data.DataView> is created from that query and bound to a <xref:System.Windows.Forms.BindingSource> object.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a><span data-ttu-id="e67c0-137">Sıralamayı Temizleme</span><span class="sxs-lookup"><span data-stu-id="e67c0-137">Clearing the Sort</span></span>  

 <span data-ttu-id="e67c0-138">Bir üzerinde sıralama bilgileri, <xref:System.Data.DataView> özelliği kullanılarak ayarlandıktan sonra temizlenir <xref:System.Data.DataView.Sort%2A> .</span><span class="sxs-lookup"><span data-stu-id="e67c0-138">The sorting information on a <xref:System.Data.DataView> can be cleared after it has been set using the <xref:System.Data.DataView.Sort%2A> property.</span></span> <span data-ttu-id="e67c0-139">İçindeki sıralama bilgilerini temizlemek için iki yol vardır <xref:System.Data.DataView> :</span><span class="sxs-lookup"><span data-stu-id="e67c0-139">There are two ways to clear the sorting information in <xref:System.Data.DataView>:</span></span>  
  
- <span data-ttu-id="e67c0-140"><xref:System.Data.DataView.Sort%2A>Özelliğini olarak ayarlayın `null` .</span><span class="sxs-lookup"><span data-stu-id="e67c0-140">Set the <xref:System.Data.DataView.Sort%2A> property to `null`.</span></span>  
  
- <span data-ttu-id="e67c0-141"><xref:System.Data.DataView.Sort%2A>Özelliği boş bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e67c0-141">Set the <xref:System.Data.DataView.Sort%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e67c0-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="e67c0-142">Example</span></span>  

 <span data-ttu-id="e67c0-143">Aşağıdaki örnek bir sorgudan bir <xref:System.Data.DataView> sorgu oluşturur ve bu özelliği boş bir dizeye ayarlayarak sıralamayı temizler <xref:System.Data.DataView.Sort%2A> :</span><span class="sxs-lookup"><span data-stu-id="e67c0-143">The following example creates a <xref:System.Data.DataView> from a query and clears the sorting by setting the <xref:System.Data.DataView.Sort%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a><span data-ttu-id="e67c0-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="e67c0-144">Example</span></span>  

 <span data-ttu-id="e67c0-145">Aşağıdaki örnek, <xref:System.Data.DataView> kişi tablosundan bir oluşturur ve <xref:System.Data.DataView.Sort%2A> özelliği, son ada göre azalan sırada sıralanacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e67c0-145">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort by last name in descending order.</span></span> <span data-ttu-id="e67c0-146">Sıralama bilgileri, özelliği şu şekilde ayarlanarak temizlenir <xref:System.Data.DataView.Sort%2A> `null` :</span><span class="sxs-lookup"><span data-stu-id="e67c0-146">The sorting information is then cleared by setting the <xref:System.Data.DataView.Sort%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a><span data-ttu-id="e67c0-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e67c0-147">See also</span></span>

- [<span data-ttu-id="e67c0-148">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e67c0-148">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="e67c0-149">DataView ile Filtreleme</span><span class="sxs-lookup"><span data-stu-id="e67c0-149">Filtering with DataView</span></span>](filtering-with-dataview-linq-to-dataset.md)
- <span data-ttu-id="e67c0-150">[Verileri Sıralama](/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e67c0-150">[Sorting Data](/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span></span>
