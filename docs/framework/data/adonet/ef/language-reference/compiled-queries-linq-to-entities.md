---
title: "Derlenmiş sorgu (LINQ to Entities)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 4cdea4d0ca5a8f7b829b9d0a99a6097d164bbf21
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="compiled-queries--linq-to-entities"></a><span data-ttu-id="8bd90-102">Derlenmiş sorgu (LINQ to Entities)</span><span class="sxs-lookup"><span data-stu-id="8bd90-102">Compiled Queries  (LINQ to Entities)</span></span>
<span data-ttu-id="8bd90-103">Entity Framework içinde birçok kez yapısal olarak benzer sorguları yürüten bir uygulamanız varsa, bir kez sorgu derleme ve farklı parametrelerle birkaç kez yürütme tarafından sık performansını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bd90-103">When you have an application that executes structurally similar queries many times in the Entity Framework, you can frequently increase performance by compiling the query one time and executing it several times with different parameters.</span></span> <span data-ttu-id="8bd90-104">Örneğin, belirli bir şehirde tüm müşteriler almak bir uygulama olabilir; Şehir çalışma zamanında bir form kullanıcı tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8bd90-104">For example, an application might have to retrieve all the customers in a particular city; the city is specified at runtime by the user in a form.</span></span> <span data-ttu-id="8bd90-105">LINQ to Entities bu amaç için derlenmiş sorgularını kullanarak destekler.</span><span class="sxs-lookup"><span data-stu-id="8bd90-105">LINQ to Entities supports using compiled queries for this purpose.</span></span>  
  
 <span data-ttu-id="8bd90-106">.NET Framework 4. 5'ile başlayarak, LINQ sorgularını otomatik olarak önbelleğe.</span><span class="sxs-lookup"><span data-stu-id="8bd90-106">Starting with the .NET Framework 4.5, LINQ queries are cached automatically.</span></span> <span data-ttu-id="8bd90-107">Ancak, sonraki yürütmeleri içinde bu maliyetini azaltmak için derlenmiş LINQ sorgularını kullanmaya devam edebilirsiniz ve derlenmiş sorguları otomatik olarak önbelleğe alınan LINQ sorgularını daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="8bd90-107">However, you can still use compiled LINQ queries to reduce this cost in later executions and compiled queries can be more efficient than LINQ queries that are automatically cached.</span></span> <span data-ttu-id="8bd90-108">LINQ to Entities sorguları Not geçerli `Enumerable.Contains` bellek içi koleksiyonlara işleci otomatik olarak önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="8bd90-108">Note that LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="8bd90-109">Ayrıca derlenmiş LINQ sorgularını bellek içi koleksiyonlarda kümesini parametreleştirme izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="8bd90-109">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
 <span data-ttu-id="8bd90-110"><xref:System.Data.Objects.CompiledQuery> Sınıfı, derleme ve yeniden kullanım için sorguları önbelleğe alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bd90-110">The <xref:System.Data.Objects.CompiledQuery> class provides compilation and caching of queries for reuse.</span></span> <span data-ttu-id="8bd90-111">Kavramsal olarak, bu sınıfı içeren bir <xref:System.Data.Objects.CompiledQuery>'s `Compile` birkaç aşırı yöntemiyle.</span><span class="sxs-lookup"><span data-stu-id="8bd90-111">Conceptually, this class contains a <xref:System.Data.Objects.CompiledQuery>'s `Compile` method with several overloads.</span></span> <span data-ttu-id="8bd90-112">Çağrı `Compile` derlenmiş sorgu temsil etmek için yeni bir temsilci oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bd90-112">Call the `Compile` method to create a new delegate to represent the compiled query.</span></span> <span data-ttu-id="8bd90-113">`Compile` İle sağlanan yöntemleri, bir <xref:System.Data.Objects.ObjectContext> ve bazı sonuç üreten bir temsilci dönüş parametre değerleri (gibi bir <xref:System.Linq.IQueryable%601> örnek).</span><span class="sxs-lookup"><span data-stu-id="8bd90-113">The `Compile` methods, provided with a <xref:System.Data.Objects.ObjectContext> and parameter values, return a delegate that produces some result (such as an <xref:System.Linq.IQueryable%601> instance).</span></span> <span data-ttu-id="8bd90-114">Sorgu bir kez yalnızca ilk yürütme sırasında derler.</span><span class="sxs-lookup"><span data-stu-id="8bd90-114">The query compiles once during only the first execution.</span></span> <span data-ttu-id="8bd90-115">Sorgu için derleme zamanında ayarlamak birleştirme seçeneklerini daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="8bd90-115">The merge options set for the query at the time of the compilation cannot be changed later.</span></span> <span data-ttu-id="8bd90-116">Sorgu derlenmiş sonra yalnızca ilkel tür parametrelerinin sağlayabilir ancak oluşturulan SQL değişeceğinden sorgunun bölümlerini değiştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="8bd90-116">Once the query is compiled you can only supply parameters of primitive type but you cannot replace parts of the query that would change the generated SQL.</span></span> <span data-ttu-id="8bd90-117">Daha fazla bilgi için bkz: [Entity Framework birleştirme seçenekleri ve derlenmiş sorguları](http://go.microsoft.com/fwlink/?LinkId=199591)</span><span class="sxs-lookup"><span data-stu-id="8bd90-117">For more information, see [Entity Framework Merge Options and Compiled Queries](http://go.microsoft.com/fwlink/?LinkId=199591)</span></span>  
  
 <span data-ttu-id="8bd90-118">[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Sorgu ifadesi, <xref:System.Data.Objects.CompiledQuery>'s `Compile` yöntemi derlerken genel biri tarafından temsil edilir `Func` gibi Temsilciler <xref:System.Func%605>.</span><span class="sxs-lookup"><span data-stu-id="8bd90-118">The [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query expression that the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method compiles is represented by one of the generic `Func` delegates, such as <xref:System.Func%605>.</span></span> <span data-ttu-id="8bd90-119">Sorgu ifadesi en fazla sarmalayabilen bir `ObjectContext` parametresi, bir dönüş parametresi ve 16 sorgu parametreleri.</span><span class="sxs-lookup"><span data-stu-id="8bd90-119">At most, the query expression can encapsulate an `ObjectContext` parameter, a return parameter, and 16 query parameters.</span></span> <span data-ttu-id="8bd90-120">16'dan fazla sorgu parametreleri gerekirse, sorgu parametreleri özellikleri temsil eden bir yapı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bd90-120">If more than 16 query parameters are required, you can create a structure whose properties represent query parameters.</span></span> <span data-ttu-id="8bd90-121">Özellikler ayarlandıktan sonra sorgu ifadesinde yapısına özelliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bd90-121">You can then use the properties on the structure in the query expression after you set the properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bd90-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd90-122">Example</span></span>  
 <span data-ttu-id="8bd90-123">Aşağıdaki örnek derler ve kabul eden bir sorgu çağıran bir <xref:System.Decimal> giriş parametresi ve toplam süre $200,00 eşit veya daha büyük olduğu siparişler bir dizi döndürür:</span><span class="sxs-lookup"><span data-stu-id="8bd90-123">The following example compiles and then invokes a query that accepts a <xref:System.Decimal> input parameter and returns a sequence of orders where the total due is greater than or equal to $200.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a><span data-ttu-id="8bd90-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd90-124">Example</span></span>  
 <span data-ttu-id="8bd90-125">Aşağıdaki örnek derler ve döndüren bir sorgu çağıran bir <xref:System.Data.Objects.ObjectQuery%601> örneği:</span><span class="sxs-lookup"><span data-stu-id="8bd90-125">The following example compiles and then invokes a query that returns an <xref:System.Data.Objects.ObjectQuery%601> instance:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a><span data-ttu-id="8bd90-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd90-126">Example</span></span>  
 <span data-ttu-id="8bd90-127">Aşağıdaki örnek derler ve ürün listesi fiyatlar ortalaması döndüren bir sorgu çağıran bir <xref:System.Decimal> değeri:</span><span class="sxs-lookup"><span data-stu-id="8bd90-127">The following example compiles and then invokes a query that returns the average of the product list prices as a <xref:System.Decimal> value:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a><span data-ttu-id="8bd90-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd90-128">Example</span></span>  
 <span data-ttu-id="8bd90-129">Aşağıdaki örnek derler ve kabul eden bir sorgu çağıran bir <xref:System.String> giriş parametresi ve döndürür bir `Contact` , e-posta adresi belirtilen dize ile başlar:</span><span class="sxs-lookup"><span data-stu-id="8bd90-129">The following example compiles and then invokes a query that accepts a <xref:System.String> input parameter and then returns a `Contact` whose email address starts with the specified string:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a><span data-ttu-id="8bd90-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd90-130">Example</span></span>  
 <span data-ttu-id="8bd90-131">Aşağıdaki örnek derler ve kabul eden bir sorgu çağırır <xref:System.DateTime> ve <xref:System.Decimal> giriş parametreleri ve bir dizi siparişleri sipariş tarihi daha sonra 8 Mart 2003'ten olduğu ve son toplam döndürür olduğu değerinden $300.00:</span><span class="sxs-lookup"><span data-stu-id="8bd90-131">The following example compiles and then invokes a query that accepts <xref:System.DateTime> and <xref:System.Decimal> input parameters and returns a sequence of orders where the order date is later than March 8, 2003, and the total due is less than $300.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a><span data-ttu-id="8bd90-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd90-132">Example</span></span>  
 <span data-ttu-id="8bd90-133">Aşağıdaki örnek derler ve kabul eden bir sorgu çağıran bir <xref:System.DateTime> giriş parametresi ve sipariş tarihi 8 Mart 2004'den sonraki olduğu siparişler bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8bd90-133">The following example compiles and then invokes a query that accepts a <xref:System.DateTime> input parameter and returns a sequence of orders where the order date is later than March 8, 2004.</span></span> <span data-ttu-id="8bd90-134">Bu sorgu anonim türdeki bir dizisi olarak sipariş bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8bd90-134">This query returns the order information as a sequence of anonymous types.</span></span> <span data-ttu-id="8bd90-135">Tür parametrelerinde belirtemezsiniz, anonim türler derleyici tarafından olayla <xref:System.Data.Objects.CompiledQuery>'s `Compile` yöntemi ve türü sorguda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8bd90-135">Anonymous types are inferred by the compiler, so you cannot specify type parameters in the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method and the type is defined in the query itself.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a><span data-ttu-id="8bd90-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bd90-136">Example</span></span>  
 <span data-ttu-id="8bd90-137">Aşağıdaki örnek, derler ve kullanıcı tanımlı yapısı giriş parametresi kabul edip siparişler bir dizi döndürür bir sorgu çağırır.</span><span class="sxs-lookup"><span data-stu-id="8bd90-137">The following example compiles and then invokes a query that accepts a user-defined structure input parameter and returns a sequence of orders.</span></span> <span data-ttu-id="8bd90-138">Başlangıç tarihi ve bitiş tarihi toplam sorgu parametreleri son yapısını tanımlar ve sorgu Mart 3 ve 8 Mart 2003 arasında $700.00 büyük son toplam ile birlikte gelen siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8bd90-138">The structure defines start date, end date, and total due query parameters, and the query returns orders shipped between March 3 and March 8, 2003 with a total due greater than $700.00.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 <span data-ttu-id="8bd90-139">Sorgu parametreleri tanımlar yapısı:</span><span class="sxs-lookup"><span data-stu-id="8bd90-139">The structure that defines the query parameters:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a><span data-ttu-id="8bd90-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd90-140">See Also</span></span>  
 [<span data-ttu-id="8bd90-141">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8bd90-141">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="8bd90-142">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="8bd90-142">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [<span data-ttu-id="8bd90-143">Entity Framework birleştirme seçeneklerini ve derlenmiş sorguları</span><span class="sxs-lookup"><span data-stu-id="8bd90-143">Entity Framework Merge Options and Compiled Queries</span></span>](http://go.microsoft.com/fwlink/?LinkId=199591)
