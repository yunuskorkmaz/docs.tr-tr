---
title: Özel birleştirme işlemleri (C# üzerinde LINQ)
description: C# dilinde özel LINQ birleştirme işlemleri gerçekleştirmeyi öğreneceksiniz.
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: a0e08396c006f68949357c50a28b3b0982f0dd83
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866682"
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="6cefa-103">Özel birleştirme işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6cefa-103">Perform custom join operations</span></span>

<span data-ttu-id="6cefa-104">Bu örnek ile mümkün olmayan birleştirme işlemleri gerçekleştirme işlemini gösterir `join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6cefa-104">This example shows how to perform join operations that aren't possible with the `join` clause.</span></span> <span data-ttu-id="6cefa-105">Bir sorgu ifadesinde `join` yan tümcesi ile sınırlıdır ve en iyi duruma getirilmiş, birleştirme işlemi arayla en yaygın olan equijoins yazın.</span><span class="sxs-lookup"><span data-stu-id="6cefa-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="6cefa-106">Equijoin gerçekleştirirken, büyük olasılıkla her zaman en iyi performansı kullanarak erişmenizi sağlayacak `join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6cefa-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>

<span data-ttu-id="6cefa-107">Ancak, `join` yan tümcesi aşağıdaki durumlarda kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="6cefa-107">However, the `join` clause cannot be used in the following cases:</span></span>

- <span data-ttu-id="6cefa-108">Ne zaman eşitsizlik (bir olmayan-equijoin) bir ifade üzerinde birleştirme predicated.</span><span class="sxs-lookup"><span data-stu-id="6cefa-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>

- <span data-ttu-id="6cefa-109">Ne zaman birleştirme eşitlik ve eşitsizlik birden fazla deyimde de predicated.</span><span class="sxs-lookup"><span data-stu-id="6cefa-109">When the join is predicated on more than one expression of equality or inequality.</span></span>

- <span data-ttu-id="6cefa-110">Ne zaman, birleştirme işleminden önce sağ tarafındaki (iç) dizisi için bir geçici aralık değişkeni Ekle gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cefa-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>

 <span data-ttu-id="6cefa-111">Equijoins olmayan birleştirmeler gerçekleştirme için birden çok kullanabilirsiniz `from` bağımsız olarak her bir veri kaynağı tanıtmak amacıyla yan tümceler.</span><span class="sxs-lookup"><span data-stu-id="6cefa-111">To perform joins that aren't equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="6cefa-112">Ardından bir koşul ifadesinde geçerli bir `where` yan tümcesinin aralık değişkeni için her kaynak.</span><span class="sxs-lookup"><span data-stu-id="6cefa-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="6cefa-113">İfade bir yöntem çağrısının form da yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cefa-113">The expression also can take the form of a method call.</span></span>

> [!NOTE]
> <span data-ttu-id="6cefa-114">Bu tür özel birleştirme işlemi birden çok kullanımıyla karıştırmayın `from` iç koleksiyonlara erişmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6cefa-114">Don't confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="6cefa-115">Daha fazla bilgi için [JOIN yan tümcesi](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6cefa-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="6cefa-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cefa-116">Example</span></span>

<span data-ttu-id="6cefa-117">İlk yöntem aşağıdaki örnekte basit bir çapraz birleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cefa-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="6cefa-118">Çok büyük sonuç kümelerinin oluşturmadığından arası birleştirmeler dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6cefa-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="6cefa-119">Ancak, bunlar karşı ek sorgular çalıştırdığınız kaynak dizileri oluşturmak için bazı senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6cefa-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>

<span data-ttu-id="6cefa-120">İkinci yöntem, bir dizi Kategori Kimliği Kategori listesinden sol tarafta listelenen tüm ürünlerin üretir.</span><span class="sxs-lookup"><span data-stu-id="6cefa-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="6cefa-121">Kullanımına dikkat edin `let` yan tümcesi ve `Contains` geçici bir dizi oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6cefa-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="6cefa-122">Sorgu önce bir dizi oluşturun ve ilk ortadan kaldırmak da mümkündür `from` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6cefa-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a><span data-ttu-id="6cefa-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cefa-123">Example</span></span>

<span data-ttu-id="6cefa-124">Aşağıdaki örnekte sorgu iç (sağ taraf) dizisi söz konusu olduğunda join tümcesi kendisini önce alınamıyor, anahtarların eşleşmesi temeline göre iki diziyi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cefa-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="6cefa-125">Bu birleştirme ile gerçekleştirilmişse bir `join` yan tümcesi, ardından `Split` her öğe için çağrılacak yöntem sahip.</span><span class="sxs-lookup"><span data-stu-id="6cefa-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="6cefa-126">Birden çok kullanımı `from` yinelenen yöntem çağrısının ek yükten kaçınmak sorgu yan tümceleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6cefa-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="6cefa-127">Ancak, bu yana `join` hala olabilir kullanarak birden çok daha hızlı bu özel durumda iyileştirilmiş `from` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="6cefa-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="6cefa-128">Sonuçlar, öncelikli olarak nasıl pahalı yöntem çağrısında olduğuna bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="6cefa-128">The results will vary depending primarily on how expensive the method call is.</span></span>

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a><span data-ttu-id="6cefa-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cefa-129">See also</span></span>

- [<span data-ttu-id="6cefa-130">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6cefa-130">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="6cefa-131">join yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="6cefa-131">join clause</span></span>](../language-reference/keywords/join-clause.md)  
- [<span data-ttu-id="6cefa-132">Join yan tümcesinin sonuçlarını sıralama</span><span class="sxs-lookup"><span data-stu-id="6cefa-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)  