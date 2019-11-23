---
title: From Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 781902f1bf28bd029c8d9825aee155a6691cbae9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004784"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="0ceb4-102">From Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ceb4-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="0ceb4-103">Bir veya daha fazla Aralık değişkenini ve sorgulanacak bir koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ceb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="0ceb4-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0ceb4-105">Parts</span></span>  
  
|<span data-ttu-id="0ceb4-106">Terim</span><span class="sxs-lookup"><span data-stu-id="0ceb4-106">Term</span></span>|<span data-ttu-id="0ceb4-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="0ceb4-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="0ceb4-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-108">Required.</span></span> <span data-ttu-id="0ceb4-109">Koleksiyonun öğeleri boyunca yinelemek için kullanılan bir *Aralık değişkeni* .</span><span class="sxs-lookup"><span data-stu-id="0ceb4-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="0ceb4-110">Sorgu `collection`üzerinde yineleme yaparken `collection` her üyesine başvurmak için bir Aralık değişkeni kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="0ceb4-111">Sıralanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="0ceb4-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-112">Optional.</span></span> <span data-ttu-id="0ceb4-113">`element` öğesinin türü.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-113">The type of `element`.</span></span> <span data-ttu-id="0ceb4-114">`type` belirtilmemişse, `element` türü `collection`algılanır.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="0ceb4-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-115">Required.</span></span> <span data-ttu-id="0ceb4-116">Sorgulanacak koleksiyona başvurur.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="0ceb4-117">Sıralanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ceb4-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ceb4-118">Remarks</span></span>  
 <span data-ttu-id="0ceb4-119">`From` yan tümcesi, bir sorgunun kaynak verilerini ve kaynak koleksiyondaki bir öğeye başvurmak için kullanılan değişkenleri belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="0ceb4-120">Bu değişkenlere *Aralık değişkenleri*denir.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-120">These variables are called *range variables*.</span></span> <span data-ttu-id="0ceb4-121">`From` yan tümcesi, bir sorgu için, yalnızca toplanmış sonuçlar döndüren bir sorguyu belirlemek için kullanılan `Aggregate` yan tümcesi dışında zorunludur.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="0ceb4-122">Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0ceb4-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="0ceb4-123">Birleştirilecek birden çok koleksiyonu belirlemek için bir sorguda birden çok `From` yan tümce belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="0ceb4-124">Birden çok koleksiyon belirtildiğinde, bunlar birbirinden bağımsız olarak yinelenir veya ilişkili olmaları durumunda bunlara katılabilirler.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="0ceb4-125">`Select` yan tümcesini kullanarak veya açıkça `Join` veya `Group Join` yan tümceleri kullanarak koleksiyonları birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="0ceb4-126">Alternatif olarak, tek bir `From` yan tümcesinde birden çok Aralık değişkeni ve koleksiyonlar belirterek, her ilgili Aralık değişkeni ve koleksiyon diğerlerinden virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="0ceb4-127">Aşağıdaki kod örneğinde `From` yan tümcesi için her iki sözdizimi seçeneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="0ceb4-128">`From` yan tümcesi, bir `For` döngüsünün kapsamına benzer bir sorgunun kapsamını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="0ceb4-129">Bu nedenle, bir sorgunun kapsamındaki her `element` Aralık değişkeni benzersiz bir ada sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="0ceb4-130">Bir sorgu için birden çok `From` yan tümce belirtebileceğiniz için, sonraki `From` yan tümceleri `From` yan tümcesindeki Aralık değişkenlerine başvurabilir veya önceki bir `From` yan tümcesindeki Aralık değişkenlerine başvurabilirler.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="0ceb4-131">Örneğin, aşağıdaki örnek, ikinci yan tümcesindeki koleksiyonun ilk yan tümcesindeki Range değişkeninin bir özelliğine dayandığı iç içe geçmiş bir `From` yan tümcesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="0ceb4-132">Her `From` yan tümcesine sorgu iyileştirmek için ek sorgu yan tümcelerinin herhangi bir birleşimi gelebilir.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="0ceb4-133">Sorguyu aşağıdaki yollarla geliştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0ceb4-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="0ceb4-134">Birden çok koleksiyonu dolaylı olarak `From` ve `Select` yan tümceleri kullanarak veya `Join` ya da `Group Join` yan tümcelerini kullanarak açıkça birleştirin.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="0ceb4-135">Sorgu sonucunu filtrelemek için `Where` yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="0ceb4-136">`Order By` yan tümcesini kullanarak sonucu sıralayın.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="0ceb4-137">Benzer sonuçları, `Group By` yan tümcesini kullanarak birlikte gruplandırın.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="0ceb4-138">Tüm sorgu sonucu için değerlendirmek üzere toplama işlevlerini belirlemek için `Aggregate` yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="0ceb4-139">Değeri bir koleksiyon yerine bir ifade tarafından belirlenen bir yineleme değişkenini tanıtmak için `Let` yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="0ceb4-140">Yinelenen sorgu sonuçlarını yoksaymak için `Distinct` yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="0ceb4-141">`Skip`, `Take`, `Skip While`ve `Take While` yan tümcelerini kullanarak döndürülecek sonuç parçalarını belirler.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ceb4-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ceb4-142">Example</span></span>  
 <span data-ttu-id="0ceb4-143">Aşağıdaki sorgu ifadesi, `customers` koleksiyonundaki her bir `Customer` nesnesi için bir Aralık değişkeni `cust` bildirmek üzere bir `From` yan tümcesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="0ceb4-144">`Where` yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="0ceb4-145">`For Each` döngüsü, sorgu sonucundaki her bir müşteri için şirket adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="0ceb4-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ceb4-146">See also</span></span>

- [<span data-ttu-id="0ceb4-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="0ceb4-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="0ceb4-148">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="0ceb4-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="0ceb4-149">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="0ceb4-150">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="0ceb4-151">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="0ceb4-152">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="0ceb4-153">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="0ceb4-154">Distinct Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="0ceb4-155">Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="0ceb4-156">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="0ceb4-157">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="0ceb4-158">Let Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="0ceb4-159">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="0ceb4-160">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="0ceb4-161">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="0ceb4-162">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0ceb4-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
