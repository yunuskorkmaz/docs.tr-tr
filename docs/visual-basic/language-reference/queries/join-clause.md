---
title: Join Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: b1551583079c66d1bf5f6963a42d5d24e518fff3
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137349"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="d5a07-102">Join Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a07-102">Join Clause (Visual Basic)</span></span>
<span data-ttu-id="d5a07-103">İki koleksiyonu tek bir koleksiyon halinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5a07-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="d5a07-104">Birleştirme işlemi anahtarların eşleşmesi temeline göre ve kullandığı `Equals` işleci.</span><span class="sxs-lookup"><span data-stu-id="d5a07-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a07-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5a07-105">Syntax</span></span>  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d5a07-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d5a07-106">Parts</span></span>  
 `element`  
 <span data-ttu-id="d5a07-107">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d5a07-107">Required.</span></span> <span data-ttu-id="d5a07-108">Denetim değişkeni birleştirilen koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d5a07-108">The control variable for the collection being joined.</span></span>  
  
 `collection`  
 <span data-ttu-id="d5a07-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d5a07-109">Required.</span></span> <span data-ttu-id="d5a07-110">Sol tarafında belirtilen toplama ile birleştirmek için koleksiyon `Join` işleci.</span><span class="sxs-lookup"><span data-stu-id="d5a07-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="d5a07-111">A `Join` yan tümcesi iç içe geçirilemez başka `Join` yan tümcesi veya bir `Group Join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d5a07-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>  
  
 `joinClause`  
 <span data-ttu-id="d5a07-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d5a07-112">Optional.</span></span> <span data-ttu-id="d5a07-113">Bir veya daha fazla ek `Join` daha da fazla yan tümce sorgu daraltın.</span><span class="sxs-lookup"><span data-stu-id="d5a07-113">One or more additional `Join` clauses to further refine the query.</span></span>  
  
 `groupJoinClause`  
 <span data-ttu-id="d5a07-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d5a07-114">Optional.</span></span> <span data-ttu-id="d5a07-115">Bir veya daha fazla ek `Group Join` daha da fazla yan tümce sorgu daraltın.</span><span class="sxs-lookup"><span data-stu-id="d5a07-115">One or more additional `Group Join` clauses to further refine the query.</span></span>  
  
 <span data-ttu-id="d5a07-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="d5a07-116">`key1` `Equals` `key2`</span></span>  
 <span data-ttu-id="d5a07-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d5a07-117">Required.</span></span> <span data-ttu-id="d5a07-118">Birleştirilen koleksiyonlar için anahtarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5a07-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="d5a07-119">Kullanmalısınız `Equals` birleştirilen koleksiyonları'ndaki anahtarları Karşılaştırılacak işleci.</span><span class="sxs-lookup"><span data-stu-id="d5a07-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="d5a07-120">Birleştirme koşulları kullanarak birleştirebilirsiniz `And` birden çok anahtar tanımlamak için işleci.</span><span class="sxs-lookup"><span data-stu-id="d5a07-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="d5a07-121">`key1` sol tarafındaki koleksiyondan olmalıdır `Join` işleci.</span><span class="sxs-lookup"><span data-stu-id="d5a07-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="d5a07-122">`key2` sağ alt tarafında koleksiyondan olmalıdır `Join` işleci.</span><span class="sxs-lookup"><span data-stu-id="d5a07-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>  
  
 <span data-ttu-id="d5a07-123">Birleşim koşulunda kullanılan anahtarları koleksiyonundan birden fazla öğe içeren ifadeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5a07-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="d5a07-124">Ancak, her anahtar ifadesi yalnızca kendi ilgili koleksiyondaki öğeler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d5a07-124">However, each key expression can contain only items from its respective collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5a07-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5a07-125">Remarks</span></span>  
 <span data-ttu-id="d5a07-126">`Join` Yan tümcesi birleştirilen koleksiyonları anahtar değerlerinden eşleşmesi temeline göre iki koleksiyon birleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5a07-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="d5a07-127">Sonuçta elde edilen koleksiyon değerleri sol tarafında belirtilen koleksiyondaki herhangi bir birleşimini içerebilir `Join` işleci ile tanımlanan koleksiyonu `Join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d5a07-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="d5a07-128">Sorgu tarafından koşulu için belirtilen sonuç döndürür `Equals` işleci karşılanıyorsa.</span><span class="sxs-lookup"><span data-stu-id="d5a07-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="d5a07-129">Bunun eşdeğeri olan bir `INNER JOIN` SQL.</span><span class="sxs-lookup"><span data-stu-id="d5a07-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="d5a07-130">Birden çok kullanabileceğiniz `Join` tek bir koleksiyon iki veya daha fazla koleksiyonlara katılmak için bir sorgu yan tümcelerinde.</span><span class="sxs-lookup"><span data-stu-id="d5a07-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>  
  
 <span data-ttu-id="d5a07-131">Koleksiyonları olmadan birleştirmek için örtük bir birleşim gerçekleştirebileceğiniz `Join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d5a07-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="d5a07-132">Bunu yapmak için birden çok dahil `In` yan tümcelerinde, `From` yan tümcesini belirtin bir `Where` birleştirme için kullanmak istediğiniz anahtarları tanımlayan yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d5a07-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>  
  
 <span data-ttu-id="d5a07-133">Kullanabileceğiniz `Group Join` koleksiyonları tek bir hiyerarşik koleksiyon halinde birleştirmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d5a07-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="d5a07-134">Bu benzer bir `LEFT OUTER JOIN` SQL.</span><span class="sxs-lookup"><span data-stu-id="d5a07-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5a07-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5a07-135">Example</span></span>  
 <span data-ttu-id="d5a07-136">Aşağıdaki kod örneği, müşterilerin listesini siparişlerini ile birleştirmek için örtük bir birleşim gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5a07-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="d5a07-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5a07-137">Example</span></span>  
 <span data-ttu-id="d5a07-138">Aşağıdaki kod örneği iki koleksiyonu kullanarak birleştirir `Join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d5a07-138">The following code example joins two collections by using the `Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 <span data-ttu-id="d5a07-139">Bu örnekte, aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d5a07-139">This example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a><span data-ttu-id="d5a07-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5a07-140">Example</span></span>  
 <span data-ttu-id="d5a07-141">Aşağıdaki kod örneği iki koleksiyonu kullanarak birleştirir `Join` iki anahtar sütunlarıyla yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d5a07-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 <span data-ttu-id="d5a07-142">Örneğin, aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d5a07-142">The example will produce output similar to the following:</span></span>  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a><span data-ttu-id="d5a07-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5a07-143">See Also</span></span>  
 [<span data-ttu-id="d5a07-144">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="d5a07-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d5a07-145">Sorgular</span><span class="sxs-lookup"><span data-stu-id="d5a07-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="d5a07-146">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d5a07-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="d5a07-147">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d5a07-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="d5a07-148">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d5a07-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="d5a07-149">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d5a07-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
