---
title: Join Tümcesi
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
ms.openlocfilehash: b0baca9f897a00b3c6c67699629477ff385d6ef7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353271"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="ed3ca-102">Join Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed3ca-102">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="ed3ca-103">İki koleksiyonu tek bir koleksiyon halinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="ed3ca-104">JOIN işlemi, eşleşen anahtarlara dayalıdır ve `Equals` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed3ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed3ca-105">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="ed3ca-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ed3ca-106">Parts</span></span>

<span data-ttu-id="ed3ca-107">`element` gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-107">`element` Required.</span></span> <span data-ttu-id="ed3ca-108">Birleştirilen koleksiyonun denetim değişkeni.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-108">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="ed3ca-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-109">Required.</span></span> <span data-ttu-id="ed3ca-110">`Join` işlecinin sol tarafında tanımlanan koleksiyonla birleştirilecek koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="ed3ca-111">`Join` yan tümcesi, başka bir `Join` yan tümcesinde veya `Group Join` yan tümcesinde iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="ed3ca-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-112">Optional.</span></span> <span data-ttu-id="ed3ca-113">Sorguyu daha da belirginleştirmek için bir veya daha fazla ek `Join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-113">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="ed3ca-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-114">Optional.</span></span> <span data-ttu-id="ed3ca-115">Sorguyu daha da belirginleştirmek için bir veya daha fazla ek `Group Join` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-115">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="ed3ca-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="ed3ca-116">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="ed3ca-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-117">Required.</span></span> <span data-ttu-id="ed3ca-118">Katılmakta olan koleksiyonlar için anahtarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="ed3ca-119">Birleştirilecek koleksiyonlardan anahtarları karşılaştırmak için `Equals` işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="ed3ca-120">Birden çok anahtarı belirlemek için `And` işlecini kullanarak Birleştirme koşullarını birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="ed3ca-121">`key1`, `Join` işlecinin sol tarafındaki koleksiyondan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="ed3ca-122">`key2`, `Join` işlecinin sağ tarafındaki koleksiyondan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="ed3ca-123">JOIN koşulunda kullanılan anahtarlar, koleksiyondan birden fazla öğe içeren ifadeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="ed3ca-124">Ancak, her anahtar ifadesi yalnızca ilgili koleksiyonundan öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-124">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed3ca-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed3ca-125">Remarks</span></span>

<span data-ttu-id="ed3ca-126">`Join` yan tümcesi, katılmakta olan koleksiyonlardan eşleşen anahtar değerlerini temel alarak iki koleksiyonu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="ed3ca-127">Elde edilen koleksiyon, `Join` işlecinin sol tarafında tanımlanan koleksiyondaki değerlerin birleşimini ve `Join` yan tümcesinde tanımlanan koleksiyonu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="ed3ca-128">Sorgu yalnızca `Equals` işleci tarafından belirtilen koşulun karşılandığı sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="ed3ca-129">Bu, SQL 'deki bir `INNER JOIN` eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="ed3ca-130">İki veya daha fazla koleksiyonu tek bir koleksiyonda birleştirmek için bir sorguda birden çok `Join` yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="ed3ca-131">`Join` yan tümcesi olmadan koleksiyonları birleştirmek için örtük bir birleştirme gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="ed3ca-132">Bunu yapmak için, `From` yan tümcesine birden çok `In` yan tümce ekleyin ve JOIN için kullanmak istediğiniz anahtarları tanımlayan bir `Where` yan tümcesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="ed3ca-133">Koleksiyonları tek bir hiyerarşik koleksiyonda birleştirmek için `Group Join` yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="ed3ca-134">Bu SQL 'de bir `LEFT OUTER JOIN` gibidir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="ed3ca-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed3ca-135">Example</span></span>

<span data-ttu-id="ed3ca-136">Aşağıdaki kod örneği, bir müşteri listesini siparişleriyle birlikte birleştirmek için örtük bir birleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="ed3ca-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed3ca-137">Example</span></span>

<span data-ttu-id="ed3ca-138">Aşağıdaki kod örneği, `Join` yan tümcesini kullanarak iki koleksiyonu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-138">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="ed3ca-139">Bu örnek aşağıdakine benzer bir çıktı oluşturacaktır:</span><span class="sxs-lookup"><span data-stu-id="ed3ca-139">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="ed3ca-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed3ca-140">Example</span></span>

<span data-ttu-id="ed3ca-141">Aşağıdaki kod örneği, `Join` yan tümcesini iki anahtar sütunla kullanarak iki koleksiyonu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="ed3ca-142">Örnek aşağıdakine benzer bir çıktı oluşturacaktır:</span><span class="sxs-lookup"><span data-stu-id="ed3ca-142">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="ed3ca-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed3ca-143">See also</span></span>

- [<span data-ttu-id="ed3ca-144">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="ed3ca-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ed3ca-145">Sorgular</span><span class="sxs-lookup"><span data-stu-id="ed3ca-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ed3ca-146">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ed3ca-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="ed3ca-147">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ed3ca-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ed3ca-148">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ed3ca-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="ed3ca-149">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="ed3ca-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
