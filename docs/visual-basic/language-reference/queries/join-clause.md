---
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
ms.openlocfilehash: f73dc31bbbb9014a8a1a315de406c53fa58d1c65
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359780"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="c273c-102">Join Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c273c-102">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="c273c-103">İki koleksiyonu tek bir koleksiyon halinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c273c-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="c273c-104">JOIN işlemi, eşleşen anahtarlara dayalıdır ve `Equals` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c273c-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="c273c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c273c-105">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="c273c-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c273c-106">Parts</span></span>

<span data-ttu-id="c273c-107">`element`Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c273c-107">`element` Required.</span></span> <span data-ttu-id="c273c-108">Birleştirilen koleksiyonun denetim değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c273c-108">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="c273c-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c273c-109">Required.</span></span> <span data-ttu-id="c273c-110">İşlecin sol tarafında tanımlanan koleksiyonla birleştirilecek koleksiyon `Join` .</span><span class="sxs-lookup"><span data-stu-id="c273c-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="c273c-111">`Join`Yan tümce, başka bir `Join` yan tümce içinde veya yan tümcesinde iç içe olabilir `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="c273c-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="c273c-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c273c-112">Optional.</span></span> <span data-ttu-id="c273c-113">`Join`Sorguyu daha da belirginleştirmek için bir veya daha fazla ek yan tümce.</span><span class="sxs-lookup"><span data-stu-id="c273c-113">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="c273c-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c273c-114">Optional.</span></span> <span data-ttu-id="c273c-115">`Group Join`Sorguyu daha da belirginleştirmek için bir veya daha fazla ek yan tümce.</span><span class="sxs-lookup"><span data-stu-id="c273c-115">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="c273c-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="c273c-116">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="c273c-117">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c273c-117">Required.</span></span> <span data-ttu-id="c273c-118">Katılmakta olan koleksiyonlar için anahtarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c273c-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="c273c-119">`Equals`Birleştirilecek koleksiyonlardan anahtarları karşılaştırmak için işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c273c-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="c273c-120">`And`Birden çok anahtarı tanımlamak için işlecini kullanarak Birleştirme koşullarını birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c273c-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="c273c-121">`key1`işlecin sol tarafındaki koleksiyondan olmalıdır `Join` .</span><span class="sxs-lookup"><span data-stu-id="c273c-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="c273c-122">`key2`işlecin sağ tarafındaki koleksiyondan olmalıdır `Join` .</span><span class="sxs-lookup"><span data-stu-id="c273c-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="c273c-123">JOIN koşulunda kullanılan anahtarlar, koleksiyondan birden fazla öğe içeren ifadeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="c273c-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="c273c-124">Ancak, her anahtar ifadesi yalnızca ilgili koleksiyonundan öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c273c-124">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="c273c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c273c-125">Remarks</span></span>

<span data-ttu-id="c273c-126">`Join`Yan tümcesi, katılmakta olan koleksiyonlardan eşleşen anahtar değerlerini temel alarak iki koleksiyonu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c273c-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="c273c-127">Elde edilen koleksiyon, işlecin sol tarafında tanımlanan koleksiyondaki değerlerin herhangi bir birleşimini `Join` ve yan tümcesinde tanımlanan koleksiyonu içerebilir `Join` .</span><span class="sxs-lookup"><span data-stu-id="c273c-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="c273c-128">Sorgu yalnızca işleç tarafından belirtilen koşulun `Equals` karşılandığı sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="c273c-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="c273c-129">Bu, bir SQL ile eşdeğerdir `INNER JOIN` .</span><span class="sxs-lookup"><span data-stu-id="c273c-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="c273c-130">`Join`İki veya daha fazla koleksiyonu tek bir koleksiyonda birleştirmek için bir sorguda birden çok yan tümce kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c273c-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="c273c-131">Yan tümce olmadan koleksiyonları birleştirmek için örtük bir birleştirme gerçekleştirebilirsiniz `Join` .</span><span class="sxs-lookup"><span data-stu-id="c273c-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="c273c-132">Bunu yapmak için, yan tümcesine birden çok yan tümce ekleyin `In` `From` ve `Where` JOIN için kullanmak istediğiniz anahtarları tanımlayan bir yan tümce belirtin.</span><span class="sxs-lookup"><span data-stu-id="c273c-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="c273c-133">`Group Join`Yan tümcesini, koleksiyonları tek bir hiyerarşik koleksiyonda birleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c273c-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="c273c-134">Bu `LEFT OUTER JOIN` SQL içindeki gibidir.</span><span class="sxs-lookup"><span data-stu-id="c273c-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="c273c-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="c273c-135">Example</span></span>

<span data-ttu-id="c273c-136">Aşağıdaki kod örneği, bir müşteri listesini siparişleriyle birlikte birleştirmek için örtük bir birleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c273c-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="c273c-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="c273c-137">Example</span></span>

<span data-ttu-id="c273c-138">Aşağıdaki kod örneği, yan tümcesini kullanarak iki koleksiyonu birleştirir `Join` .</span><span class="sxs-lookup"><span data-stu-id="c273c-138">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="c273c-139">Bu örnek aşağıdakine benzer bir çıktı oluşturacaktır:</span><span class="sxs-lookup"><span data-stu-id="c273c-139">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="c273c-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="c273c-140">Example</span></span>

<span data-ttu-id="c273c-141">Aşağıdaki kod örneği, `Join` iki anahtar sütunu olan yan tümcesini kullanarak iki koleksiyonu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c273c-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="c273c-142">Örnek aşağıdakine benzer bir çıktı oluşturacaktır:</span><span class="sxs-lookup"><span data-stu-id="c273c-142">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="c273c-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c273c-143">See also</span></span>

- [<span data-ttu-id="c273c-144">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="c273c-144">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c273c-145">Sorgular</span><span class="sxs-lookup"><span data-stu-id="c273c-145">Queries</span></span>](index.md)
- [<span data-ttu-id="c273c-146">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c273c-146">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="c273c-147">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c273c-147">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="c273c-148">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="c273c-148">Group Join Clause</span></span>](group-join-clause.md)
- [<span data-ttu-id="c273c-149">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c273c-149">Where Clause</span></span>](where-clause.md)
