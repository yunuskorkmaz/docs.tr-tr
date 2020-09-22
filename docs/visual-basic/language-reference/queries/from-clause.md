---
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
ms.openlocfilehash: 120ba6da11bffc3a0e81873d1fd606633724723d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875248"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="216b8-102">From Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="216b8-102">From Clause (Visual Basic)</span></span>

<span data-ttu-id="216b8-103">Bir veya daha fazla Aralık değişkenini ve sorgulanacak bir koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="216b8-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="216b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="216b8-104">Syntax</span></span>  
  
```vb  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="216b8-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="216b8-105">Parts</span></span>  
  
|<span data-ttu-id="216b8-106">Terim</span><span class="sxs-lookup"><span data-stu-id="216b8-106">Term</span></span>|<span data-ttu-id="216b8-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="216b8-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="216b8-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="216b8-108">Required.</span></span> <span data-ttu-id="216b8-109">Koleksiyonun öğeleri boyunca yinelemek için kullanılan bir *Aralık değişkeni* .</span><span class="sxs-lookup"><span data-stu-id="216b8-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="216b8-110">Bir Aralık değişkeni, `collection` sorgu ile yineleme yaparken öğesinin her üyesine başvurmak için kullanılır `collection` .</span><span class="sxs-lookup"><span data-stu-id="216b8-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="216b8-111">Sıralanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="216b8-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="216b8-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="216b8-112">Optional.</span></span> <span data-ttu-id="216b8-113">Türü `element` .</span><span class="sxs-lookup"><span data-stu-id="216b8-113">The type of `element`.</span></span> <span data-ttu-id="216b8-114">Hayır `type` belirtilmemişse, türü `element` öğesinden çıkarsanamıyor `collection` .</span><span class="sxs-lookup"><span data-stu-id="216b8-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="216b8-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="216b8-115">Required.</span></span> <span data-ttu-id="216b8-116">Sorgulanacak koleksiyona başvurur.</span><span class="sxs-lookup"><span data-stu-id="216b8-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="216b8-117">Sıralanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="216b8-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="216b8-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="216b8-118">Remarks</span></span>  

 <span data-ttu-id="216b8-119">`From`Yan tümcesi, bir sorgunun kaynak verilerini ve kaynak koleksiyondaki bir öğeye başvurmak için kullanılan değişkenleri belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="216b8-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="216b8-120">Bu değişkenlere *Aralık değişkenleri*denir.</span><span class="sxs-lookup"><span data-stu-id="216b8-120">These variables are called *range variables*.</span></span> <span data-ttu-id="216b8-121">Yan tümcesi, `From` bir sorgu için, `Aggregate` yan tümcesinin yalnızca toplanmış sonuçları döndüren bir sorguyu belirlemek için kullanılması dışında, gereklidir.</span><span class="sxs-lookup"><span data-stu-id="216b8-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="216b8-122">Daha fazla bilgi için bkz. [toplama yan tümcesi](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="216b8-122">For more information, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="216b8-123">`From`Birleştirilecek birden çok koleksiyonu belirlemek için bir sorguda birden çok yan tümce belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="216b8-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="216b8-124">Birden çok koleksiyon belirtildiğinde, bunlar birbirinden bağımsız olarak yinelenir veya ilişkili olmaları durumunda bunlara katılabilirler.</span><span class="sxs-lookup"><span data-stu-id="216b8-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="216b8-125">`Select`Yan tümcesini kullanarak veya açıkça `Join` veya yan tümceleri kullanarak koleksiyonları birleştirebilirsiniz `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="216b8-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="216b8-126">Alternatif olarak, tek bir yan tümce içinde birden fazla Aralık değişkeni ve koleksiyonlar belirterek `From` , her ilgili Aralık değişkeni ve koleksiyon diğerlerinden virgülle ayırarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="216b8-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="216b8-127">Aşağıdaki kod örneğinde yan tümce için her iki sözdizimi seçeneği gösterilmektedir `From` .</span><span class="sxs-lookup"><span data-stu-id="216b8-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="216b8-128">`From`Yan tümcesi, bir döngünün kapsamına benzer bir sorgunun kapsamını tanımlar `For` .</span><span class="sxs-lookup"><span data-stu-id="216b8-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="216b8-129">Bu nedenle, `element` bir sorgunun kapsamındaki her Aralık değişkeninin benzersiz bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="216b8-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="216b8-130">`From`Bir sorgu için birden çok yan tümce belirtebileceğiniz için, sonraki `From` yan tümceler yan tümcesindeki Aralık değişkenlerine başvurabilir `From` veya bir önceki yan tümcedeki Aralık değişkenlerine başvurabilirler `From` .</span><span class="sxs-lookup"><span data-stu-id="216b8-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="216b8-131">Örneğin, aşağıdaki örnek, `From` ikinci yan tümcesindeki koleksiyonun ilk yan tümcesindeki Range değişkeninin bir özelliğine dayandığı iç içe geçmiş bir yan tümce gösterir.</span><span class="sxs-lookup"><span data-stu-id="216b8-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="216b8-132">Her `From` yan tümce, sorguyu iyileştirmek için ek sorgu yan tümcelerinin herhangi bir birleşimi tarafından izlenebilir.</span><span class="sxs-lookup"><span data-stu-id="216b8-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="216b8-133">Sorguyu aşağıdaki yollarla geliştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="216b8-133">You can refine the query in the following ways:</span></span>  
  
- <span data-ttu-id="216b8-134">`From`Ve `Select` yan tümcelerini kullanarak veya açıkça `Join` veya `Group Join` yan tümceleri kullanarak birden çok koleksiyonu örtülü olarak birleştirin.</span><span class="sxs-lookup"><span data-stu-id="216b8-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
- <span data-ttu-id="216b8-135">`Where`Sorgu sonucunu filtrelemek için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="216b8-135">Use the `Where` clause to filter the query result.</span></span>  
  
- <span data-ttu-id="216b8-136">Yan tümcesini kullanarak sonucu sıralayın `Order By` .</span><span class="sxs-lookup"><span data-stu-id="216b8-136">Sort the result by using the `Order By` clause.</span></span>  
  
- <span data-ttu-id="216b8-137">Yan tümcesini kullanarak benzer sonuçları birlikte gruplandırın `Group By` .</span><span class="sxs-lookup"><span data-stu-id="216b8-137">Group similar results together by using the `Group By` clause.</span></span>  
  
- <span data-ttu-id="216b8-138">`Aggregate`Tüm sorgu sonucu için değerlendirmek üzere toplama işlevlerini belirlemek için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="216b8-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
- <span data-ttu-id="216b8-139">`Let`Değeri bir koleksiyon yerine bir ifade tarafından belirlenen bir yineleme değişkeni tanıtmak için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="216b8-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
- <span data-ttu-id="216b8-140">`Distinct`Yinelenen sorgu sonuçlarını yoksaymak için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="216b8-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
- <span data-ttu-id="216b8-141">,, `Skip` `Take` `Skip While` , Ve `Take While` yan tümceleri kullanarak döndürülecek sonuç parçalarını belirler.</span><span class="sxs-lookup"><span data-stu-id="216b8-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="216b8-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="216b8-142">Example</span></span>  

 <span data-ttu-id="216b8-143">Aşağıdaki sorgu ifadesi, `From` koleksiyondaki her bir nesne için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `cust` `Customer` `customers` .</span><span class="sxs-lookup"><span data-stu-id="216b8-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="216b8-144">`Where`Yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="216b8-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="216b8-145">`For Each`Döngü, sorgu sonucunda her müşteri için şirket adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="216b8-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="216b8-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="216b8-146">See also</span></span>

- [<span data-ttu-id="216b8-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="216b8-147">Queries</span></span>](index.md)
- [<span data-ttu-id="216b8-148">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="216b8-148">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="216b8-149">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="216b8-149">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="216b8-150">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="216b8-150">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="216b8-151">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-151">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="216b8-152">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-152">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="216b8-153">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-153">Aggregate Clause</span></span>](aggregate-clause.md)
- [<span data-ttu-id="216b8-154">Distinct Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-154">Distinct Clause</span></span>](distinct-clause.md)
- [<span data-ttu-id="216b8-155">JOIN yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="216b8-156">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-156">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="216b8-157">Order by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-157">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="216b8-158">Let yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-158">Let Clause</span></span>](let-clause.md)
- [<span data-ttu-id="216b8-159">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-159">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="216b8-160">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-160">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="216b8-161">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-161">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="216b8-162">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="216b8-162">Take While Clause</span></span>](take-while-clause.md)
