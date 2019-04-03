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
ms.openlocfilehash: b18ef2f291e20d8a150972a980ba063377b0bc3a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839619"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="62be8-102">From Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62be8-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="62be8-103">Bir veya daha fazla aralık değişkenleri ve bir sorgu koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="62be8-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62be8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62be8-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="62be8-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="62be8-105">Parts</span></span>  
  
|<span data-ttu-id="62be8-106">Terim</span><span class="sxs-lookup"><span data-stu-id="62be8-106">Term</span></span>|<span data-ttu-id="62be8-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="62be8-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="62be8-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="62be8-108">Required.</span></span> <span data-ttu-id="62be8-109">A *aralık değişkeni* koleksiyon öğelerinde yineleme yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62be8-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="62be8-110">Aralık değişkeni için her üye için kullanılır `collection` sorgu gezinir gibi `collection`.</span><span class="sxs-lookup"><span data-stu-id="62be8-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="62be8-111">Sıralanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62be8-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="62be8-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="62be8-112">Optional.</span></span> <span data-ttu-id="62be8-113">Türünü `element`.</span><span class="sxs-lookup"><span data-stu-id="62be8-113">The type of `element`.</span></span> <span data-ttu-id="62be8-114">Hayır ise `type` belirtilen türü `element` içinden gösterilen `collection`.</span><span class="sxs-lookup"><span data-stu-id="62be8-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="62be8-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="62be8-115">Required.</span></span> <span data-ttu-id="62be8-116">Koleksiyona sorgulanacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="62be8-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="62be8-117">Sıralanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62be8-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62be8-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62be8-118">Remarks</span></span>  
 <span data-ttu-id="62be8-119">`From` Yan tümcesi bir sorgu ve kaynak koleksiyonu bir öğesine başvurmak için kullanılan değişkenleri için kaynak verilerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62be8-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="62be8-120">Bu değişkenleri olarak adlandırılmasının *aralık değişkenleri*.</span><span class="sxs-lookup"><span data-stu-id="62be8-120">These variables are called *range variables*.</span></span> <span data-ttu-id="62be8-121">`From` Aşağıdakiler haricinde bir sorgu yan tümcesi gereklidir `Aggregate` yan tümcesi döndürür yalnızca toplu sonuçları, bir sorgu tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62be8-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="62be8-122">Daha fazla bilgi için [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="62be8-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="62be8-123">Birden çok belirtebilirsiniz `From` birleştirilecek olan birden çok koleksiyon belirlemek üzere bir sorgu yan tümcelerinde.</span><span class="sxs-lookup"><span data-stu-id="62be8-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="62be8-124">Birden çok koleksiyon belirtildiğinde, bunlar üzerinden bağımsız olarak yinelendiğinde veya ilişkili oldukları varsa bunları birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62be8-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="62be8-125">Kullanarak, örtük olarak bir koleksiyonları birleştirebilirsiniz `Select` yan tümcesi kullanılarak açık şekilde veya `Join` veya `Group Join` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="62be8-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="62be8-126">Alternatif olarak, birden çok aralık değişkenleri ve Koleksiyonlar tek bir belirtebilirsiniz `From` her ilgili aralık değişkeni ve diğerlerinden virgülle ayırarak toplama yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62be8-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="62be8-127">Aşağıdaki kod örneği her iki sözdizimi seçeneklerini gösterir `From` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62be8-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="62be8-128">`From` Yan tümcesi bir sorgu kapsamına benzer kapsamını tanımlar bir `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="62be8-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="62be8-129">Bu nedenle, her `element` aralık değişkeni bir sorgu kapsamında benzersiz adlara sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="62be8-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="62be8-130">Birden çok belirtebildiğinizden `From` izleyen bir sorgu için yan tümceler `From` yan tümceleri aralık değişkenleri başvurabilir `From` yan tümcesi veya başvurabilir aralık değişkenleri önceki `From` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62be8-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="62be8-131">Örneğin, aşağıdaki örnekte iç içe bir gösterir `From` burada ikinci yan tümcesinde toplama temel bir özelliği birinci yan tümce de Aralık değişkeninin yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62be8-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="62be8-132">Her `From` yan tümcesi sorguyu daraltmak için ek sorgu yan tümceleri herhangi bir birleşimi tarafından takip.</span><span class="sxs-lookup"><span data-stu-id="62be8-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="62be8-133">Sorgu aşağıdaki yollarla daraltabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="62be8-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="62be8-134">Örtük olarak kullanarak birden çok koleksiyon birleştirme `From` ve `Select` yan tümcesi kullanılarak açık şekilde veya `Join` veya `Group Join` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="62be8-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="62be8-135">Kullanım `Where` sorgu sonucu filtrelemek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62be8-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="62be8-136">Sonuç kullanarak sıralama `Order By` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62be8-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="62be8-137">Şuna benzer sonuçlar gruplamak kullanarak `Group By` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62be8-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="62be8-138">Kullanım `Aggregate` yan tümcesi için tüm sorgu sonucu değerlendiremedik toplama işlevleri tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="62be8-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="62be8-139">Kullanım `Let` yan tanıtan bir yineleme değişkeninin değeri ifade yerine bir koleksiyona göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="62be8-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="62be8-140">Kullanım `Distinct` yan yinelenen sorgu sonuçları yoksay.</span><span class="sxs-lookup"><span data-stu-id="62be8-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="62be8-141">Kullanarak, döndürülecek sonuç parçalarını tanımlamak `Skip`, `Take`, `Skip While`, ve `Take While` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="62be8-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62be8-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="62be8-142">Example</span></span>  
 <span data-ttu-id="62be8-143">Aşağıdaki sorgu ifadesi kullanan bir `From` yan tümcesinin aralık değişkenini bildirmek için `cust` her `Customer` nesnesine `customers` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="62be8-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="62be8-144">`Where` Yan tümcesi, çıkış belirtilen bölgeden müşterilere kısıtlamak için aralık değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="62be8-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="62be8-145">`For Each` Döngü, her müşteri için şirket adı sorgu sonucu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="62be8-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="62be8-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62be8-146">See also</span></span>

- [<span data-ttu-id="62be8-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="62be8-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="62be8-148">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="62be8-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="62be8-149">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="62be8-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="62be8-150">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="62be8-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="62be8-151">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="62be8-152">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="62be8-153">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="62be8-154">Distinct Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="62be8-155">Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="62be8-156">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="62be8-157">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="62be8-158">Let Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="62be8-159">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="62be8-160">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="62be8-161">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="62be8-162">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="62be8-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
