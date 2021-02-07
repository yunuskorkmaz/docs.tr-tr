---
description: 'Hakkında daha fazla bilgi edinin: DataView ile sıralama (LINQ to DataSet)'
title: DataView ile sıralama (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: ac07e5bc2c74a5724a4497d630d7352694ac9a7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718687"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a><span data-ttu-id="626b8-103">DataView ile sıralama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="626b8-103">Sorting with DataView (LINQ to DataSet)</span></span>

<span data-ttu-id="626b8-104">Verileri belirli ölçütlere göre sıralama ve sonra verileri bir kullanıcı arabirimi denetimi aracılığıyla bir istemciye sunma özelliği, veri bağlamanın önemli bir yönüdür.</span><span class="sxs-lookup"><span data-stu-id="626b8-104">The ability to sort data based on specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="626b8-105"><xref:System.Data.DataView> verileri sıralamak ve belirli sıralama ölçütlerine göre sıralanmış veri satırlarını döndürmek için çeşitli yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="626b8-105"><xref:System.Data.DataView> provides several ways to sort data and return data rows ordered by specific ordering criteria.</span></span> <span data-ttu-id="626b8-106">Dize tabanlı sıralama yeteneklerine ek olarak, <xref:System.Data.DataView> Sıralama ölçütleri için Language-Integrated Query (LINQ) ifadelerini de kullanmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="626b8-106">In addition to its string-based sorting capabilities, <xref:System.Data.DataView> also enables you to use Language-Integrated Query (LINQ) expressions for the sorting criteria.</span></span> <span data-ttu-id="626b8-107">LINQ ifadeleri, dize tabanlı sıralamaya kıyasla çok daha karmaşık ve güçlü sıralama işlemlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="626b8-107">LINQ expressions allow for much more complex and powerful sorting operations than string-based sorting.</span></span> <span data-ttu-id="626b8-108">Bu konuda, kullanarak sıralama için her iki yaklaşım da açıklanmaktadır <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="626b8-108">This topic describes both approaches to sorting using <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a><span data-ttu-id="626b8-109">Sıralama bilgileriyle bir sorgudan DataView oluşturma</span><span class="sxs-lookup"><span data-stu-id="626b8-109">Creating DataView from a Query with Sorting Information</span></span>  

 <span data-ttu-id="626b8-110">Bir <xref:System.Data.DataView> nesne, bir LINQ to DataSet sorgusundan oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="626b8-110">A <xref:System.Data.DataView> object can be created from a LINQ to DataSet query.</span></span> <span data-ttu-id="626b8-111">Bu sorgu bir,, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> <xref:System.Linq.Enumerable.ThenBy%2A> veya <xref:System.Linq.Enumerable.ThenByDescending%2A> yan tümce içeriyorsa, bu yan tümcelerdeki ifadeler, içindeki verileri sıralamaya yönelik temel olarak kullanılır <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="626b8-111">If that query contains an <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, or <xref:System.Linq.Enumerable.ThenByDescending%2A> clause the expressions in these clauses are used as the basis for sorting the data in the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="626b8-112">Örneğin, sorgu `Order By…` ve `Then By…` yan tümceleri içeriyorsa, sonuçta <xref:System.Data.DataView> verileri belirtilen her iki sütuna göre sıraya alır.</span><span class="sxs-lookup"><span data-stu-id="626b8-112">For example, if the query contains the `Order By…`and `Then By…` clauses, the resulting <xref:System.Data.DataView> would order the data by both columns specified.</span></span>  
  
 <span data-ttu-id="626b8-113">İfade tabanlı sıralama, daha basit dize tabanlı sıralamaya kıyasla daha güçlü ve karmaşık sıralama sağlar.</span><span class="sxs-lookup"><span data-stu-id="626b8-113">Expression-based sorting offers more powerful and complex sorting than the simpler string-based sorting.</span></span> <span data-ttu-id="626b8-114">Dize tabanlı ve ifade tabanlı sıralamanın birbirini dışlamadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="626b8-114">Note that string-based and expression-based sorting are mutually exclusive.</span></span> <span data-ttu-id="626b8-115">Dize tabanlı, bir <xref:System.Data.DataView.Sort%2A> sorgudan oluşturulduktan sonra ayarlandıysa <xref:System.Data.DataView> , sorgudan çıkarılan ifade tabanlı filtre temizlenir ve sıfırlanamaz.</span><span class="sxs-lookup"><span data-stu-id="626b8-115">If the string-based <xref:System.Data.DataView.Sort%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression-based filter inferred from the query is cleared and cannot be reset.</span></span>  
  
 <span data-ttu-id="626b8-116">' A ait dizin, <xref:System.Data.DataView> her ikisi de <xref:System.Data.DataView> oluşturulduğunda ve sıralama ya da filtreleme bilgisi değiştirildiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="626b8-116">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="626b8-117">Tarafından oluşturulan LINQ to DataSet sorgusunda sıralama ölçütlerini sağlayarak en iyi performansı elde edersiniz <xref:System.Data.DataView> ve sıralama bilgilerini daha sonra değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="626b8-117">You get the best performance by supplying sorting criteria in the LINQ to DataSet query that the <xref:System.Data.DataView> is created from and not modifying the sorting information, later.</span></span> <span data-ttu-id="626b8-118">Daha fazla bilgi için bkz. [DataView performansı](dataview-performance.md).</span><span class="sxs-lookup"><span data-stu-id="626b8-118">For more information, see [DataView Performance](dataview-performance.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="626b8-119">Çoğu durumda, sıralama için kullanılan ifadelerin yan etkileri olmaması ve belirleyici olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="626b8-119">In most cases, the expressions used for sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="626b8-120">Ayrıca, sıralama işlemleri herhangi bir sayıda yürütülene kadar, ifadeler bir dizi yürütme sayısına bağlı herhangi bir mantığı içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="626b8-120">Also, the expressions should not contain any logic that depends on a set number of executions, because the sorting operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="626b8-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="626b8-121">Example</span></span>  

 <span data-ttu-id="626b8-122">Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırları sipariş tarihine göre sıralar; <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' <xref:System.Data.DataView> a bağlar <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="626b8-122">The following example queries the SalesOrderHeader table and orders the returned rows by the order date; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a><span data-ttu-id="626b8-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="626b8-123">Example</span></span>  

 <span data-ttu-id="626b8-124">Aşağıdaki örnek, SalesOrderHeader tablosunu sorgular ve döndürülen satırı toplam tutara göre sıralar; <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' <xref:System.Data.DataView> a bağlar <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="626b8-124">The following example queries the SalesOrderHeader table and orders the returned row by total amount due; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a><span data-ttu-id="626b8-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="626b8-125">Example</span></span>  

 <span data-ttu-id="626b8-126">Aşağıdaki örnek, SalesOrderDetail tablosunu sorgular ve döndürülen satırları sipariş miktarına göre ve satış siparişi koduna göre sıralar; <xref:System.Data.DataView> Bu sorgudan bir oluşturur ve ' <xref:System.Data.DataView> a bağlar <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="626b8-126">The following example queries the SalesOrderDetail table and orders the returned rows by order quantity and then by sales order ID; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a><span data-ttu-id="626b8-127">String-Based Sort özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="626b8-127">Using the String-Based Sort Property</span></span>  

 <span data-ttu-id="626b8-128">Dize tabanlı sıralama işlevselliği <xref:System.Data.DataView> LINQ to DataSet ile hala işe yarar.</span><span class="sxs-lookup"><span data-stu-id="626b8-128">The string-based sorting functionality of <xref:System.Data.DataView> still works with LINQ to DataSet.</span></span> <span data-ttu-id="626b8-129">Bir LINQ to DataSet sorgusundan oluşturulduktan sonra, <xref:System.Data.DataView> <xref:System.Data.DataView.Sort%2A> üzerinde sıralamayı ayarlamak için özelliğini kullanabilirsiniz <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="626b8-129">After a <xref:System.Data.DataView> has been created from a LINQ to DataSet query, you can use the <xref:System.Data.DataView.Sort%2A> property to set the sorting on the <xref:System.Data.DataView>.</span></span>  
  
 <span data-ttu-id="626b8-130">Dize tabanlı ve ifade tabanlı sıralama işlevselliği birbirini dışlıyor.</span><span class="sxs-lookup"><span data-stu-id="626b8-130">The string-based and expression-based sorting functionality are mutually exclusive.</span></span> <span data-ttu-id="626b8-131">Özelliği ayarlandığında <xref:System.Data.DataView.Sort%2A> , tarafından oluşturulan sorgudan devralınan ifade tabanlı sıralama temizlenir <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="626b8-131">Setting the <xref:System.Data.DataView.Sort%2A> property will clear the expression-based sort inherited from the query that the <xref:System.Data.DataView> was created from.</span></span>  
  
 <span data-ttu-id="626b8-132">Dize tabanlı filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView.Sort%2A> bkz. [verileri sıralama ve filtreleme](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="626b8-132">For more information about string-based <xref:System.Data.DataView.Sort%2A> filtering, see [Sorting and Filtering Data](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="626b8-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="626b8-133">Example</span></span>  

 <span data-ttu-id="626b8-134">Takip eden örnek, <xref:System.Data.DataView> kişi tablosundan bir oluşturur ve satırları son ada göre azalan düzende sıralar, ardından ilk adı artan sırada yapar:</span><span class="sxs-lookup"><span data-stu-id="626b8-134">The follow example creates a <xref:System.Data.DataView> from the Contact table and sorts the rows by last name in descending order, then first name in ascending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a><span data-ttu-id="626b8-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="626b8-135">Example</span></span>  

 <span data-ttu-id="626b8-136">Aşağıdaki örnek, "S" harfiyle başlayan son adlarla Ilgili kişi tablosunu sorgular.</span><span class="sxs-lookup"><span data-stu-id="626b8-136">The following example queries the Contact table for last names that start with the letter "S".</span></span>  <span data-ttu-id="626b8-137"><xref:System.Data.DataView>Bu sorgudan oluşturulur ve bir <xref:System.Windows.Forms.BindingSource> nesneye bağlanır.</span><span class="sxs-lookup"><span data-stu-id="626b8-137">A <xref:System.Data.DataView> is created from that query and bound to a <xref:System.Windows.Forms.BindingSource> object.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a><span data-ttu-id="626b8-138">Sıralamayı Temizleme</span><span class="sxs-lookup"><span data-stu-id="626b8-138">Clearing the Sort</span></span>  

 <span data-ttu-id="626b8-139">Bir üzerinde sıralama bilgileri, <xref:System.Data.DataView> özelliği kullanılarak ayarlandıktan sonra temizlenir <xref:System.Data.DataView.Sort%2A> .</span><span class="sxs-lookup"><span data-stu-id="626b8-139">The sorting information on a <xref:System.Data.DataView> can be cleared after it has been set using the <xref:System.Data.DataView.Sort%2A> property.</span></span> <span data-ttu-id="626b8-140">İçindeki sıralama bilgilerini temizlemek için iki yol vardır <xref:System.Data.DataView> :</span><span class="sxs-lookup"><span data-stu-id="626b8-140">There are two ways to clear the sorting information in <xref:System.Data.DataView>:</span></span>  
  
- <span data-ttu-id="626b8-141"><xref:System.Data.DataView.Sort%2A>Özelliğini olarak ayarlayın `null` .</span><span class="sxs-lookup"><span data-stu-id="626b8-141">Set the <xref:System.Data.DataView.Sort%2A> property to `null`.</span></span>  
  
- <span data-ttu-id="626b8-142"><xref:System.Data.DataView.Sort%2A>Özelliği boş bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="626b8-142">Set the <xref:System.Data.DataView.Sort%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="626b8-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="626b8-143">Example</span></span>  

 <span data-ttu-id="626b8-144">Aşağıdaki örnek bir sorgudan bir <xref:System.Data.DataView> sorgu oluşturur ve bu özelliği boş bir dizeye ayarlayarak sıralamayı temizler <xref:System.Data.DataView.Sort%2A> :</span><span class="sxs-lookup"><span data-stu-id="626b8-144">The following example creates a <xref:System.Data.DataView> from a query and clears the sorting by setting the <xref:System.Data.DataView.Sort%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a><span data-ttu-id="626b8-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="626b8-145">Example</span></span>  

 <span data-ttu-id="626b8-146">Aşağıdaki örnek, <xref:System.Data.DataView> kişi tablosundan bir oluşturur ve <xref:System.Data.DataView.Sort%2A> özelliği, son ada göre azalan sırada sıralanacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="626b8-146">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort by last name in descending order.</span></span> <span data-ttu-id="626b8-147">Sıralama bilgileri, özelliği şu şekilde ayarlanarak temizlenir <xref:System.Data.DataView.Sort%2A> `null` :</span><span class="sxs-lookup"><span data-stu-id="626b8-147">The sorting information is then cleared by setting the <xref:System.Data.DataView.Sort%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a><span data-ttu-id="626b8-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="626b8-148">See also</span></span>

- [<span data-ttu-id="626b8-149">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="626b8-149">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="626b8-150">DataView ile Filtreleme</span><span class="sxs-lookup"><span data-stu-id="626b8-150">Filtering with DataView</span></span>](filtering-with-dataview-linq-to-dataset.md)
- <span data-ttu-id="626b8-151">[Verileri Sıralama](/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="626b8-151">[Sorting Data](/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span></span>
