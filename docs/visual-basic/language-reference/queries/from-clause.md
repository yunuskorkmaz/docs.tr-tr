---
description: 'Daha fazla bilgi edinin: from tümcesi (Visual Basic)'
title: From Yan Tümcesi
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
ms.openlocfilehash: e35188412deb7fd9f2d8306c85057d050a60d030
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700565"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="e892a-103">From Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e892a-103">From Clause (Visual Basic)</span></span>

<span data-ttu-id="e892a-104">Bir veya daha fazla Aralık değişkenini ve sorgulanacak bir koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e892a-104">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e892a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e892a-105">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e892a-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e892a-106">Parts</span></span>  
  
|<span data-ttu-id="e892a-107">Süre</span><span class="sxs-lookup"><span data-stu-id="e892a-107">Term</span></span>|<span data-ttu-id="e892a-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="e892a-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="e892a-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e892a-109">Required.</span></span> <span data-ttu-id="e892a-110">Koleksiyonun öğeleri boyunca yinelemek için kullanılan bir *Aralık değişkeni* .</span><span class="sxs-lookup"><span data-stu-id="e892a-110">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="e892a-111">Bir Aralık değişkeni, `collection` sorgu ile yineleme yaparken öğesinin her üyesine başvurmak için kullanılır `collection` .</span><span class="sxs-lookup"><span data-stu-id="e892a-111">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="e892a-112">Sıralanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e892a-112">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="e892a-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e892a-113">Optional.</span></span> <span data-ttu-id="e892a-114">Türü `element` .</span><span class="sxs-lookup"><span data-stu-id="e892a-114">The type of `element`.</span></span> <span data-ttu-id="e892a-115">Hayır `type` belirtilmemişse, türü `element` öğesinden çıkarsanamıyor `collection` .</span><span class="sxs-lookup"><span data-stu-id="e892a-115">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="e892a-116">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e892a-116">Required.</span></span> <span data-ttu-id="e892a-117">Sorgulanacak koleksiyona başvurur.</span><span class="sxs-lookup"><span data-stu-id="e892a-117">Refers to the collection to be queried.</span></span> <span data-ttu-id="e892a-118">Sıralanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e892a-118">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e892a-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e892a-119">Remarks</span></span>  

 <span data-ttu-id="e892a-120">`From`Yan tümcesi, bir sorgunun kaynak verilerini ve kaynak koleksiyondaki bir öğeye başvurmak için kullanılan değişkenleri belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e892a-120">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="e892a-121">Bu değişkenlere *Aralık değişkenleri* denir.</span><span class="sxs-lookup"><span data-stu-id="e892a-121">These variables are called *range variables*.</span></span> <span data-ttu-id="e892a-122">Yan tümcesi, `From` bir sorgu için, `Aggregate` yan tümcesinin yalnızca toplanmış sonuçları döndüren bir sorguyu belirlemek için kullanılması dışında, gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e892a-122">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="e892a-123">Daha fazla bilgi için bkz. [toplama yan tümcesi](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e892a-123">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="e892a-124">`From`Birleştirilecek birden çok koleksiyonu belirlemek için bir sorguda birden çok yan tümce belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e892a-124">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="e892a-125">Birden çok koleksiyon belirtildiğinde, bunlar birbirinden bağımsız olarak yinelenir veya ilişkili olmaları durumunda bunlara katılabilirler.</span><span class="sxs-lookup"><span data-stu-id="e892a-125">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="e892a-126">`Select`Yan tümcesini kullanarak veya açıkça `Join` veya yan tümceleri kullanarak koleksiyonları birleştirebilirsiniz `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="e892a-126">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="e892a-127">Alternatif olarak, tek bir yan tümce içinde birden fazla Aralık değişkeni ve koleksiyonlar belirterek `From` , her ilgili Aralık değişkeni ve koleksiyon diğerlerinden virgülle ayırarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e892a-127">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="e892a-128">Aşağıdaki kod örneğinde yan tümce için her iki sözdizimi seçeneği gösterilmektedir `From` .</span><span class="sxs-lookup"><span data-stu-id="e892a-128">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="e892a-129">`From`Yan tümcesi, bir döngünün kapsamına benzer bir sorgunun kapsamını tanımlar `For` .</span><span class="sxs-lookup"><span data-stu-id="e892a-129">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="e892a-130">Bu nedenle, `element` bir sorgunun kapsamındaki her Aralık değişkeninin benzersiz bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e892a-130">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="e892a-131">`From`Bir sorgu için birden çok yan tümce belirtebileceğiniz için, sonraki `From` yan tümceler yan tümcesindeki Aralık değişkenlerine başvurabilir `From` veya bir önceki yan tümcedeki Aralık değişkenlerine başvurabilirler `From` .</span><span class="sxs-lookup"><span data-stu-id="e892a-131">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="e892a-132">Örneğin, aşağıdaki örnek, `From` ikinci yan tümcesindeki koleksiyonun ilk yan tümcesindeki Range değişkeninin bir özelliğine dayandığı iç içe geçmiş bir yan tümce gösterir.</span><span class="sxs-lookup"><span data-stu-id="e892a-132">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="e892a-133">Her `From` yan tümce, sorguyu iyileştirmek için ek sorgu yan tümcelerinin herhangi bir birleşimi tarafından izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="e892a-133">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="e892a-134">Sorguyu aşağıdaki yollarla geliştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e892a-134">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="e892a-135">`From`Ve `Select` yan tümcelerini kullanarak veya açıkça `Join` veya `Group Join` yan tümceleri kullanarak birden çok koleksiyonu örtülü olarak birleştirin.</span><span class="sxs-lookup"><span data-stu-id="e892a-135">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="e892a-136">`Where`Sorgu sonucunu filtrelemek için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e892a-136">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="e892a-137">Yan tümcesini kullanarak sonucu sıralayın `Order By` .</span><span class="sxs-lookup"><span data-stu-id="e892a-137">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="e892a-138">Yan tümcesini kullanarak benzer sonuçları birlikte gruplandırın `Group By` .</span><span class="sxs-lookup"><span data-stu-id="e892a-138">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="e892a-139">`Aggregate`Tüm sorgu sonucu için değerlendirmek üzere toplama işlevlerini belirlemek için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e892a-139">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="e892a-140">`Let`Değeri bir koleksiyon yerine bir ifade tarafından belirlenen bir yineleme değişkeni tanıtmak için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e892a-140">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="e892a-141">`Distinct`Yinelenen sorgu sonuçlarını yoksaymak için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e892a-141">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="e892a-142">,, `Skip` `Take` `Skip While` , Ve `Take While` yan tümceleri kullanarak döndürülecek sonuç parçalarını belirler.</span><span class="sxs-lookup"><span data-stu-id="e892a-142">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e892a-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="e892a-143">Example</span></span>  

 <span data-ttu-id="e892a-144">Aşağıdaki sorgu ifadesi, `From` koleksiyondaki her bir nesne için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `cust` `Customer` `customers` .</span><span class="sxs-lookup"><span data-stu-id="e892a-144">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="e892a-145">`Where`Yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e892a-145">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="e892a-146">`For Each`Döngü, sorgu sonucunda her müşteri için şirket adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e892a-146">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="e892a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e892a-147">See also</span></span>

- [<span data-ttu-id="e892a-148">Sorgular</span><span class="sxs-lookup"><span data-stu-id="e892a-148">Queries</span></span>](index.md)
- [<span data-ttu-id="e892a-149">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="e892a-149">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="e892a-150">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="e892a-150">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="e892a-151">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="e892a-151">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="e892a-152">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-152">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="e892a-153">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-153">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="e892a-154">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-154">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="e892a-155">Distinct Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-155">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="e892a-156">JOIN yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-156">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="e892a-157">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-157">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="e892a-158">Order by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-158">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="e892a-159">Let yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-159">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="e892a-160">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-160">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="e892a-161">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-161">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="e892a-162">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-162">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="e892a-163">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="e892a-163">Take While Clause</span></span>](take-while-clause.md)
