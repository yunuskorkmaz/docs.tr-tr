---
title: "Özel birleştirme işlemleri gerçekleştirme"
description: "Özel birleştirme işlemleri gerçekleştirme."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: fef146c92a5cbbf21f8f1688f221c2bd45c99de7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="77dea-104">Özel birleştirme işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="77dea-104">Perform custom join operations</span></span>

<span data-ttu-id="77dea-105">Bu örnek ile mümkün olmayan birleştirme işlemleri gerçekleştirme gösterilmektedir `join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="77dea-105">This example shows how to perform join operations that are not possible with the `join` clause.</span></span> <span data-ttu-id="77dea-106">Bir sorgu ifadesinde `join` yan tümcesi sınırlıdır ve en iyi duruma getirilmiş, bunun en yaygın equijoins birleştirme işlemi yazın.</span><span class="sxs-lookup"><span data-stu-id="77dea-106">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="77dea-107">Equijoin gerçekleştirirken, büyük olasılıkla her zaman en iyi performansı kullanarak hatalarla `join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="77dea-107">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>  
  
 <span data-ttu-id="77dea-108">Ancak, `join` yan tümcesi aşağıdaki durumlarda kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="77dea-108">However, the `join` clause cannot be used in the following cases:</span></span>  
  
-   <span data-ttu-id="77dea-109">Ne zaman birleştirme eşitsizlik (bir harici-equijoin) ifadeye bağlı predicated.</span><span class="sxs-lookup"><span data-stu-id="77dea-109">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>  
  
-   <span data-ttu-id="77dea-110">Ne zaman birleştirme üzerinde eşitlik veya eşitsizlik birden fazla ifade predicated.</span><span class="sxs-lookup"><span data-stu-id="77dea-110">When the join is predicated on more than one expression of equality or inequality.</span></span>  
  
-   <span data-ttu-id="77dea-111">Birleştirme işlemi önce sağ tarafında (iç) sırası için geçici aralık değişkeni tanıtmak olduğunda.</span><span class="sxs-lookup"><span data-stu-id="77dea-111">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>  
  
 <span data-ttu-id="77dea-112">Equijoins olmayan birleştirmeler gerçekleştirmek için birden çok kullanabilirsiniz `from` bağımsız olarak her veri kaynağı tanıtmak için yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="77dea-112">To perform joins that are not equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="77dea-113">Ardından bir koşul ifadesi geçerli bir `where` yan tümcesine her kaynak için aralık değişkeni.</span><span class="sxs-lookup"><span data-stu-id="77dea-113">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="77dea-114">İfade bir yöntem çağrısı form da alabilir.</span><span class="sxs-lookup"><span data-stu-id="77dea-114">The expression also can take the form of a method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77dea-115">Bu tür bir özel birleştirme işlemi birden çok kullanımı ile karıştırmayın `from` iç koleksiyonları erişmek için yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="77dea-115">Do not confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="77dea-116">Daha fazla bilgi için bkz: [JOIN yan tümcesi](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="77dea-116">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77dea-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="77dea-117">Example</span></span>  
 <span data-ttu-id="77dea-118">İlk yöntem aşağıdaki örnekte basit bir çapraz birleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="77dea-118">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="77dea-119">Çok büyük sonuç kümeleri oluşturdukları olduğundan çapraz birleştirmeler dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77dea-119">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="77dea-120">Ancak, bunlar karşı ek sorgular çalıştırdığınız kaynak sıraları oluşturmak için bazı senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="77dea-120">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>  
  
 <span data-ttu-id="77dea-121">İkinci yöntem kategorisi Kimliğine sol tarafındaki kategori listesinde listelenen tüm ürünleri dizisi üretir.</span><span class="sxs-lookup"><span data-stu-id="77dea-121">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="77dea-122">Kullanımına dikkat edin `let` yan tümcesi ve `Contains` geçici bir dizi oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77dea-122">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="77dea-123">Sorgu önce dizi oluşturmak ve ilk ortadan kaldırmak mümkündür `from` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="77dea-123">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="77dea-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="77dea-124">Example</span></span>  
 <span data-ttu-id="77dea-125">Aşağıdaki örnekte sorgu, iç (sağ tarafta) dizisi söz konusu olduğunda JOIN yan tümcesi önce kendisini alınamıyor anahtarları eşleşmesini temel alan iki sıraları katılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="77dea-125">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="77dea-126">Bu katılımı ile gerçekleştirilen varsa bir `join` yan tümcesi, sonra `Split` yöntemi her öğe için çağrılacak sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="77dea-126">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="77dea-127">Birden çok kullanımını `from` yan tümceleri yinelenen yöntem çağrısının yükünü önlemek sorgu sağlar.</span><span class="sxs-lookup"><span data-stu-id="77dea-127">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="77dea-128">Ancak, bu yana `join` bunu hala olabilir birden çok kullanarak daha hızlı bu özel durumda iyileştirilmiş `from` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="77dea-128">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="77dea-129">Sonuçları öncelikle nasıl pahalı yöntem çağrısının olduğuna bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="77dea-129">The results will vary depending primarily on how expensive the method call is.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="77dea-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77dea-130">See also</span></span>  
 [<span data-ttu-id="77dea-131">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="77dea-131">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="77dea-132">Join tümcesi</span><span class="sxs-lookup"><span data-stu-id="77dea-132">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="77dea-133">Join tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="77dea-133">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)
