---
description: 'Daha fazla bilgi edinin: JOIN tümcesi (Visual Basic)'
title: Join Yan Tümcesi
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
ms.openlocfilehash: 69d808e68a32b3f8799dabbbc8abc53acae42b57
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700448"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="9b3e1-103">Join Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b3e1-103">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="9b3e1-104">İki koleksiyonu tek bir koleksiyon halinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-104">Combines two collections into a single collection.</span></span> <span data-ttu-id="9b3e1-105">JOIN işlemi, eşleşen anahtarlara dayalıdır ve `Equals` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-105">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b3e1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b3e1-106">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="9b3e1-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9b3e1-107">Parts</span></span>

<span data-ttu-id="9b3e1-108">`element` Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-108">`element` Required.</span></span> <span data-ttu-id="9b3e1-109">Birleştirilen koleksiyonun denetim değişkeni.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-109">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="9b3e1-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-110">Required.</span></span> <span data-ttu-id="9b3e1-111">İşlecin sol tarafında tanımlanan koleksiyonla birleştirilecek koleksiyon `Join` .</span><span class="sxs-lookup"><span data-stu-id="9b3e1-111">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="9b3e1-112">`Join`Yan tümce, başka bir `Join` yan tümce içinde veya yan tümcesinde iç içe olabilir `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="9b3e1-112">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="9b3e1-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-113">Optional.</span></span> <span data-ttu-id="9b3e1-114">`Join`Sorguyu daha da belirginleştirmek için bir veya daha fazla ek yan tümce.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-114">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="9b3e1-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-115">Optional.</span></span> <span data-ttu-id="9b3e1-116">`Group Join`Sorguyu daha da belirginleştirmek için bir veya daha fazla ek yan tümce.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-116">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="9b3e1-117">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="9b3e1-117">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="9b3e1-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-118">Required.</span></span> <span data-ttu-id="9b3e1-119">Katılmakta olan koleksiyonlar için anahtarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-119">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="9b3e1-120">`Equals`Birleştirilecek koleksiyonlardan anahtarları karşılaştırmak için işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-120">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="9b3e1-121">`And`Birden çok anahtarı tanımlamak için işlecini kullanarak Birleştirme koşullarını birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-121">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="9b3e1-122">`key1` işlecin sol tarafındaki koleksiyondan olmalıdır `Join` .</span><span class="sxs-lookup"><span data-stu-id="9b3e1-122">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="9b3e1-123">`key2` işlecin sağ tarafındaki koleksiyondan olmalıdır `Join` .</span><span class="sxs-lookup"><span data-stu-id="9b3e1-123">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="9b3e1-124">JOIN koşulunda kullanılan anahtarlar, koleksiyondan birden fazla öğe içeren ifadeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-124">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="9b3e1-125">Ancak, her anahtar ifadesi yalnızca ilgili koleksiyonundan öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-125">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b3e1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b3e1-126">Remarks</span></span>

<span data-ttu-id="9b3e1-127">`Join`Yan tümcesi, katılmakta olan koleksiyonlardan eşleşen anahtar değerlerini temel alarak iki koleksiyonu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-127">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="9b3e1-128">Elde edilen koleksiyon, işlecin sol tarafında tanımlanan koleksiyondaki değerlerin herhangi bir birleşimini `Join` ve yan tümcesinde tanımlanan koleksiyonu içerebilir `Join` .</span><span class="sxs-lookup"><span data-stu-id="9b3e1-128">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="9b3e1-129">Sorgu yalnızca işleç tarafından belirtilen koşulun `Equals` karşılandığı sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-129">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="9b3e1-130">Bu, bir SQL ile eşdeğerdir `INNER JOIN` .</span><span class="sxs-lookup"><span data-stu-id="9b3e1-130">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="9b3e1-131">`Join`İki veya daha fazla koleksiyonu tek bir koleksiyonda birleştirmek için bir sorguda birden çok yan tümce kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-131">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="9b3e1-132">Yan tümce olmadan koleksiyonları birleştirmek için örtük bir birleştirme gerçekleştirebilirsiniz `Join` .</span><span class="sxs-lookup"><span data-stu-id="9b3e1-132">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="9b3e1-133">Bunu yapmak için, yan tümcesine birden çok yan tümce ekleyin `In` `From` ve `Where` JOIN için kullanmak istediğiniz anahtarları tanımlayan bir yan tümce belirtin.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-133">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="9b3e1-134">`Group Join`Yan tümcesini, koleksiyonları tek bir hiyerarşik koleksiyonda birleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-134">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="9b3e1-135">Bu `LEFT OUTER JOIN` SQL içindeki gibidir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-135">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="9b3e1-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b3e1-136">Example</span></span>

<span data-ttu-id="9b3e1-137">Aşağıdaki kod örneği, bir müşteri listesini siparişleriyle birlikte birleştirmek için örtük bir birleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-137">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="9b3e1-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b3e1-138">Example</span></span>

<span data-ttu-id="9b3e1-139">Aşağıdaki kod örneği, yan tümcesini kullanarak iki koleksiyonu birleştirir `Join` .</span><span class="sxs-lookup"><span data-stu-id="9b3e1-139">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="9b3e1-140">Bu örnek aşağıdakine benzer bir çıktı oluşturacaktır:</span><span class="sxs-lookup"><span data-stu-id="9b3e1-140">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="9b3e1-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b3e1-141">Example</span></span>

<span data-ttu-id="9b3e1-142">Aşağıdaki kod örneği, `Join` iki anahtar sütunu olan yan tümcesini kullanarak iki koleksiyonu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-142">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="9b3e1-143">Örnek aşağıdakine benzer bir çıktı oluşturacaktır:</span><span class="sxs-lookup"><span data-stu-id="9b3e1-143">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="9b3e1-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b3e1-144">See also</span></span>

- [<span data-ttu-id="9b3e1-145">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="9b3e1-145">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="9b3e1-146">Sorgular</span><span class="sxs-lookup"><span data-stu-id="9b3e1-146">Queries</span></span>](index.md)
- [<span data-ttu-id="9b3e1-147">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="9b3e1-147">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="9b3e1-148">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="9b3e1-148">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="9b3e1-149">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="9b3e1-149">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="9b3e1-150">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="9b3e1-150">Where Clause</span></span>](where-clause.md)
