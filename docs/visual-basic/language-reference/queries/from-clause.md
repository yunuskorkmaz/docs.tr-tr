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
ms.openlocfilehash: 1f113444efae83de7d299db330593937c7800bb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604724"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="602fa-102">From Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="602fa-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="602fa-103">Bir veya daha fazla aralık değişkeni ve sorgu bir koleksiyona belirtir.</span><span class="sxs-lookup"><span data-stu-id="602fa-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="602fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="602fa-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="602fa-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="602fa-105">Parts</span></span>  
  
|<span data-ttu-id="602fa-106">Terim</span><span class="sxs-lookup"><span data-stu-id="602fa-106">Term</span></span>|<span data-ttu-id="602fa-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="602fa-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="602fa-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="602fa-108">Required.</span></span> <span data-ttu-id="602fa-109">A *aralık değişkeni* koleksiyonu öğelerinde yineleme yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="602fa-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="602fa-110">Aralık değişkeni için her üye başvurmak için kullanılan `collection` sorgu dolaşır gibi `collection`.</span><span class="sxs-lookup"><span data-stu-id="602fa-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="602fa-111">Bir numaralandırma türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="602fa-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="602fa-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="602fa-112">Optional.</span></span> <span data-ttu-id="602fa-113">Türü `element`.</span><span class="sxs-lookup"><span data-stu-id="602fa-113">The type of `element`.</span></span> <span data-ttu-id="602fa-114">Öyle değilse `type` belirtilirse, türü `element` gelen olayla `collection`.</span><span class="sxs-lookup"><span data-stu-id="602fa-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="602fa-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="602fa-115">Required.</span></span> <span data-ttu-id="602fa-116">Sorgulanacak koleksiyona ifade eder.</span><span class="sxs-lookup"><span data-stu-id="602fa-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="602fa-117">Bir numaralandırma türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="602fa-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="602fa-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="602fa-118">Remarks</span></span>  
 <span data-ttu-id="602fa-119">`From` Yan tümcesi, bir sorgu ve kaynak koleksiyondan bir öğe olarak başvurmak için kullanılan değişkenler için kaynak verilerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="602fa-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="602fa-120">Bu değişkenler adlı *aralık değişkenleri*.</span><span class="sxs-lookup"><span data-stu-id="602fa-120">These variables are called *range variables*.</span></span> <span data-ttu-id="602fa-121">`From` Ne zaman dışında bir sorgu için yan tümcesi gereklidir `Aggregate` yan tümcesi döndürür yalnızca sonuçları birleşik bir sorgu tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="602fa-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="602fa-122">Daha fazla bilgi için bkz: [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="602fa-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="602fa-123">Birden çok belirtebilirsiniz `From` birleştirilecek olan birden çok koleksiyon tanımlayacak bir sorgu yan tümcelerinde.</span><span class="sxs-lookup"><span data-stu-id="602fa-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="602fa-124">Birden çok koleksiyon belirtildiğinde, bunlar üzerinden bağımsız olarak yinelendiğinde veya ilişkili oldukları varsa bunları katılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="602fa-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="602fa-125">Kullanarak koleksiyonları örtük olarak birleştirebilirsiniz `Select` yan tümcesi veya kullanarak açıkça `Join` veya `Group Join` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="602fa-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="602fa-126">Alternatif olarak, birden çok aralık değişkeni ve koleksiyonları tek bir belirtebilirsiniz `From` yan tümcesi, her ilgili aralık değişkeni ve diğerlerinden virgülle ayrılmış koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="602fa-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="602fa-127">Aşağıdaki kod örneği iki sözdizimi seçeneklerini gösterir `From` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="602fa-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 <span data-ttu-id="602fa-128">`From` Yan tümcesi kapsamına benzer bir sorgu kapsamını tanımlayan bir `For` döngü.</span><span class="sxs-lookup"><span data-stu-id="602fa-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="602fa-129">Bu nedenle, her `element` aralık değişkeni bir sorgu kapsamında benzersiz bir adı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="602fa-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="602fa-130">Birden çok belirtebildiğinizden `From` sonraki bir sorgu için tümcecikleri `From` yan tümceleri aralık değişkenlerinin başvurabilir `From` yan tümcesi veya başvurabilir aralık değişkeni için önceki bir `From` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="602fa-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="602fa-131">Örneğin, aşağıdaki örnekte bir iç içe gösterir `From` burada ikinci tümce koleksiyonunda temel bir özelliğe ilk yan tümcesinde Aralık değişkeninin yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="602fa-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 <span data-ttu-id="602fa-132">Her `From` yan tümcesi herhangi bir bileşimini sorguyu daraltmak için ek sorgu yan tümceleri takip.</span><span class="sxs-lookup"><span data-stu-id="602fa-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="602fa-133">Sorgu aşağıdaki yollarla tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="602fa-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="602fa-134">Birden çok koleksiyon örtük olarak kullanarak birleştirme `From` ve `Select` yan tümceleri, veya kullanarak açıkça `Join` veya `Group Join` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="602fa-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="602fa-135">Kullanım `Where` sorgu sonucu filtrelemek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="602fa-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="602fa-136">Sonuç kullanarak sıralama `Order By` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="602fa-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="602fa-137">Benzer sonuçlar gruplamak kullanarak `Group By` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="602fa-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="602fa-138">Kullanım `Aggregate` için tüm sorgu sonucu değerlendirmek için toplama işlevleri tanımlamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="602fa-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="602fa-139">Kullanım `Let` değerini bir deyim bir koleksiyon yerine belirlenir bir yineleme değişkeni tanıtmak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="602fa-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="602fa-140">Kullanım `Distinct` yinelenen sorgu sonuçları yoksaymak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="602fa-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="602fa-141">Kullanarak döndürülecek sonuç parçalarını tanımlamak `Skip`, `Take`, `Skip While`, ve `Take While` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="602fa-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="602fa-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="602fa-142">Example</span></span>  
 <span data-ttu-id="602fa-143">Aşağıdaki sorgu ifade kullanan bir `From` yan tümcesinin aralık değişkeni bildirmek için `cust` her `Customer` nesnesinde `customers` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="602fa-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="602fa-144">`Where` Yan tümcesi, çıkış müşterilere belirtilen bölgesinden kısıtlamak için aralık değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="602fa-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="602fa-145">`For Each` Döngü sorgu sonucunda her müşteri için şirket adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="602fa-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="602fa-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="602fa-146">See Also</span></span>  
 [<span data-ttu-id="602fa-147">Sorgular</span><span class="sxs-lookup"><span data-stu-id="602fa-147">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="602fa-148">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="602fa-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="602fa-149">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="602fa-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="602fa-150">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="602fa-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="602fa-151">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="602fa-152">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="602fa-153">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="602fa-154">Distinct Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="602fa-155">Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="602fa-156">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="602fa-157">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="602fa-158">Let Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="602fa-159">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="602fa-160">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="602fa-161">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="602fa-162">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="602fa-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
