---
title: Özel birleştirme işlemleri gerçekleştirin (C#'da LINQ)
description: C#'da özel LINQ birleştirme işlemlerini nasıl gerçekleştireceklerini öğrenin.
ms.date: 12/01/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 7051007c67bd64cd11ede2f4d5352ce3d497255f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659858"
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="19fde-103">Özel birleştirme işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="19fde-103">Perform custom join operations</span></span>

<span data-ttu-id="19fde-104">Bu örnek, `join` yan tümceyle mümkün olmayan birleştirme işlemlerinin nasıl gerçekleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19fde-104">This example shows how to perform join operations that aren't possible with the `join` clause.</span></span> <span data-ttu-id="19fde-105">Sorgu ifadesinde, `join` yan tümce, açık ara en yaygın birleştirme işlemi türü olan equijoins ile sınırlıdır ve bunlar için en iyi duruma getirilir.</span><span class="sxs-lookup"><span data-stu-id="19fde-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="19fde-106">Bir equijoin gerçekleştirirken, büyük olasılıkla her zaman `join` yan tümceyi kullanarak en iyi performansı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="19fde-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>

<span data-ttu-id="19fde-107">Ancak, `join` yan tümce aşağıdaki durumlarda kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="19fde-107">However, the `join` clause cannot be used in the following cases:</span></span>

- <span data-ttu-id="19fde-108">Birleştirme eşitsizlik ifadesine (eşit olmayan bir şey) dayanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="19fde-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>

- <span data-ttu-id="19fde-109">Birleştirme birden fazla eşitlik veya eşitsizlik ifadesine dayanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="19fde-109">When the join is predicated on more than one expression of equality or inequality.</span></span>

- <span data-ttu-id="19fde-110">Birleştirme işleminden önce sağ taraf (iç) dizisi için geçici bir aralık değişkeni getirmeniz gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="19fde-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>

 <span data-ttu-id="19fde-111">Denk olmayan birleştirmeler gerçekleştirmek için, her veri kaynağını `from` bağımsız olarak tanıtmak için birden çok yan tümce kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19fde-111">To perform joins that aren't equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="19fde-112">Daha sonra her kaynak için `where` aralık değişkenine bir yan tümcedeki yüklem ifadesini uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="19fde-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="19fde-113">İfade de bir yöntem çağrısı şeklinde alabilir.</span><span class="sxs-lookup"><span data-stu-id="19fde-113">The expression also can take the form of a method call.</span></span>

> [!NOTE]
> <span data-ttu-id="19fde-114">Bu tür özel birleştirme işlemini iç koleksiyonlara `from` erişmek için birden çok yan tümcenin kullanılmasıyla karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="19fde-114">Don't confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="19fde-115">Daha fazla bilgi için [ara yan tümcesi'ne](../language-reference/keywords/join-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="19fde-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="19fde-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="19fde-116">Example</span></span>

<span data-ttu-id="19fde-117">Aşağıdaki örnekteki ilk yöntem basit bir çapraz birleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="19fde-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="19fde-118">Çapraz birleştirmeler, çok büyük sonuç kümeleri oluşturabildiklerinden dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="19fde-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="19fde-119">Ancak, ek sorguların çalıştırıldığı kaynak dizileri oluşturmak için bazı senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="19fde-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>

<span data-ttu-id="19fde-120">İkinci yöntem, kategori kimliği sol taraftaki kategori listesinde listelenen tüm ürünlerin bir dizisini üretir.</span><span class="sxs-lookup"><span data-stu-id="19fde-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="19fde-121">Geçici bir dizi `let` oluşturmak `Contains` için yan tümcenin ve yöntemin kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="19fde-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="19fde-122">Ayrıca, sorgudan önce dizi oluşturmak ve ilk `from` yan tümceyi ortadan kaldırmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="19fde-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a><span data-ttu-id="19fde-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="19fde-123">Example</span></span>

<span data-ttu-id="19fde-124">Aşağıdaki örnekte, sorgunun, iç (sağ taraf) dizisinde birleştirme yan tümcesi kendisinden önce alınamayan eşleşen tuşlara dayalı iki diziyi birleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="19fde-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="19fde-125">Bu birleştirme bir `join` yan tümceyle `Split` gerçekleştirildiyse, yöntemin her öğe için çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="19fde-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="19fde-126">Birden çok `from` yan tümcenin kullanılması, sorgunun yinelenen yöntem çağrısının ek yükünden kaçınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="19fde-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="19fde-127">Ancak, `join` en iyi duruma geldiğinden, bu özel durumda `from` yine de birden çok yan tümce yi kullanmaktan daha hızlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="19fde-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="19fde-128">Sonuçlar, öncelikle yöntem çağrısının ne kadar pahalı olduğuna bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="19fde-128">The results will vary depending primarily on how expensive the method call is.</span></span>

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a><span data-ttu-id="19fde-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19fde-129">See also</span></span>

- [<span data-ttu-id="19fde-130">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="19fde-130">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="19fde-131">birleştirme yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="19fde-131">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="19fde-132">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="19fde-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)
