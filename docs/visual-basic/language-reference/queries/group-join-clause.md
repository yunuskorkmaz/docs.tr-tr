---
description: 'Daha fazla bilgi edinin: Group JOIN tümcesi (Visual Basic)'
title: Group Join Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 177dc2b41c923bc8c1ae0477c3905e8adad36fbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700487"
---
# <a name="group-join-clause-visual-basic"></a><span data-ttu-id="f1775-103">Group Join Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1775-103">Group Join Clause (Visual Basic)</span></span>

<span data-ttu-id="f1775-104">İki koleksiyonu tek bir hiyerarşik koleksiyonda birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f1775-104">Combines two collections into a single hierarchical collection.</span></span> <span data-ttu-id="f1775-105">JOIN işlemi, eşleşen anahtarları temel alır.</span><span class="sxs-lookup"><span data-stu-id="f1775-105">The join operation is based on matching keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1775-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f1775-106">Syntax</span></span>  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="f1775-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f1775-107">Parts</span></span>  
  
|<span data-ttu-id="f1775-108">Süre</span><span class="sxs-lookup"><span data-stu-id="f1775-108">Term</span></span>|<span data-ttu-id="f1775-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="f1775-109">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="f1775-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1775-110">Required.</span></span> <span data-ttu-id="f1775-111">Birleştirilen koleksiyonun denetim değişkeni.</span><span class="sxs-lookup"><span data-stu-id="f1775-111">The control variable for the collection being joined.</span></span>|  
|`type`|<span data-ttu-id="f1775-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f1775-112">Optional.</span></span> <span data-ttu-id="f1775-113">Türü `element` .</span><span class="sxs-lookup"><span data-stu-id="f1775-113">The type of `element`.</span></span> <span data-ttu-id="f1775-114">Hayır `type` belirtilmemişse, türü `element` öğesinden çıkarsanamıyor `collection` .</span><span class="sxs-lookup"><span data-stu-id="f1775-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="f1775-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1775-115">Required.</span></span> <span data-ttu-id="f1775-116">İşlecin sol tarafındaki koleksiyonla birleştirilecek koleksiyon `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="f1775-116">The collection to combine with the collection that is on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="f1775-117">`Group Join`Yan tümce bir `Join` yan tümce veya başka bir yan tümce içinde iç içe olabilir `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="f1775-117">A `Group Join` clause can be nested in a `Join` clause or in another `Group Join` clause.</span></span>|  
|<span data-ttu-id="f1775-118">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="f1775-118">`key1` `Equals` `key2`</span></span>|<span data-ttu-id="f1775-119">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1775-119">Required.</span></span> <span data-ttu-id="f1775-120">Katılmakta olan koleksiyonlar için anahtarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f1775-120">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="f1775-121">`Equals`Birleştirilecek koleksiyonlardan anahtarları karşılaştırmak için işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1775-121">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="f1775-122">`And`Birden çok anahtarı tanımlamak için işlecini kullanarak Birleştirme koşullarını birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1775-122">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="f1775-123">`key1`Parametrenin, işlecin sol tarafındaki koleksiyondan olması gerekir `Join` .</span><span class="sxs-lookup"><span data-stu-id="f1775-123">The `key1` parameter must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="f1775-124">`key2`Parametrenin, işlecin sağ tarafındaki koleksiyondan olması gerekir `Join` .</span><span class="sxs-lookup"><span data-stu-id="f1775-124">The `key2` parameter must be from the collection on the right side of the `Join` operator.</span></span><br /><br /> <span data-ttu-id="f1775-125">JOIN koşulunda kullanılan anahtarlar, koleksiyondan birden fazla öğe içeren ifadeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1775-125">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="f1775-126">Ancak, her anahtar ifadesi yalnızca ilgili koleksiyonundan öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f1775-126">However, each key expression can contain only items from its respective collection.</span></span>|  
|`expressionList`|<span data-ttu-id="f1775-127">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1775-127">Required.</span></span> <span data-ttu-id="f1775-128">Koleksiyondan öğe gruplarının nasıl toplanacağına ilişkin bir veya daha fazla ifade.</span><span class="sxs-lookup"><span data-stu-id="f1775-128">One or more expressions that identify how the groups of elements from the collection are aggregated.</span></span> <span data-ttu-id="f1775-129">Gruplanmış sonuçların üye adını belirlemek için `Group` () anahtar sözcüğünü kullanın `<alias> = Group` .</span><span class="sxs-lookup"><span data-stu-id="f1775-129">To identify a member name for the grouped results, use the `Group` keyword (`<alias> = Group`).</span></span> <span data-ttu-id="f1775-130">Gruba uygulanacak toplama işlevlerini de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1775-130">You can also include aggregate functions to apply to the group.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1775-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1775-131">Remarks</span></span>  

 <span data-ttu-id="f1775-132">`Group Join`Yan tümcesi, katılmakta olan koleksiyonlardan eşleşen anahtar değerlerini temel alarak iki koleksiyonu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f1775-132">The `Group Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="f1775-133">Elde edilen koleksiyon, ikinci koleksiyondaki bir öğe koleksiyonuna başvuran ve ilk koleksiyondaki anahtar değeriyle eşleşen bir üye içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f1775-133">The resulting collection can contain a member that references a collection of elements from the second collection that match the key value from the first collection.</span></span> <span data-ttu-id="f1775-134">İkinci koleksiyondaki gruplanmış öğelere uygulanacak toplama işlevlerini de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1775-134">You can also specify aggregate functions to apply to the grouped elements from the second collection.</span></span> <span data-ttu-id="f1775-135">Toplama işlevleri hakkında bilgi için bkz. [Aggregate yan tümcesi](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f1775-135">For information about aggregate functions, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="f1775-136">Örneğin, bir grup yönetici ve bir çalışan koleksiyonu gibi düşünün.</span><span class="sxs-lookup"><span data-stu-id="f1775-136">Consider, for example, a collection of managers and a collection of employees.</span></span> <span data-ttu-id="f1775-137">Her iki koleksiyonun öğesi, belirli bir yöneticiye rapor veren çalışanları tanımlayan bir ManagerID özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f1775-137">Elements from both collections have a ManagerID property that identifies the employees that report to a particular manager.</span></span> <span data-ttu-id="f1775-138">Bir JOIN işleminin sonuçları, eşleşen bir ManagerID değeri olan her yönetici ve çalışan için sonuç içerir.</span><span class="sxs-lookup"><span data-stu-id="f1775-138">The results from a join operation would contain a result for each manager and employee with a matching ManagerID value.</span></span> <span data-ttu-id="f1775-139">Bir işlemin sonuçları, `Group Join` yöneticilerin tüm listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f1775-139">The results from a `Group Join` operation would contain the complete list of managers.</span></span> <span data-ttu-id="f1775-140">Her yöneticinin sonucu, belirli bir yönetici için eşleşme olan çalışanların listesine başvuran bir üyeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="f1775-140">Each manager result would have a member that referenced the list of employees that were a match for the specific manager.</span></span>  
  
 <span data-ttu-id="f1775-141">Bir işlemden kaynaklanan koleksiyon, `Group Join` yan tümcelerinde tanımlanan koleksiyondan `From` ve yan tümce içinde tanımlanan ifadelerde herhangi bir değer birleşimini içerebilir `Into` `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="f1775-141">The collection resulting from a `Group Join` operation can contain any combination of values from the collection identified in the `From` clause and the expressions identified in the `Into` clause of the `Group Join` clause.</span></span> <span data-ttu-id="f1775-142">Yan tümce için geçerli ifadeler hakkında daha fazla bilgi için `Into` bkz. [Aggregate yan tümcesi](aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f1775-142">For more information about valid expressions for the `Into` clause, see [Aggregate Clause](aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="f1775-143">Bir `Group Join` işlem, işlecin sol tarafında tanımlanan koleksiyondaki tüm sonuçları döndürür `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="f1775-143">A `Group Join` operation will return all results from the collection identified on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="f1775-144">Bu, toplanmakta olan koleksiyonda eşleşme olmaması durumunda da geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f1775-144">This is true even if there are no matches in the collection being joined.</span></span> <span data-ttu-id="f1775-145">Bu `LEFT OUTER JOIN` SQL içindeki gibidir.</span><span class="sxs-lookup"><span data-stu-id="f1775-145">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="f1775-146">`Join`Yan tümcesini kullanarak koleksiyonları tek bir koleksiyon içinde birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1775-146">You can use the `Join` clause to combine collections into a single collection.</span></span> <span data-ttu-id="f1775-147">Bu, bir SQL ile eşdeğerdir `INNER JOIN` .</span><span class="sxs-lookup"><span data-stu-id="f1775-147">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1775-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1775-148">Example</span></span>  

 <span data-ttu-id="f1775-149">Aşağıdaki kod örneği, yan tümcesini kullanarak iki koleksiyonu birleştirir `Group Join` .</span><span class="sxs-lookup"><span data-stu-id="f1775-149">The following code example joins two collections by using the `Group Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="f1775-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1775-150">See also</span></span>

- [<span data-ttu-id="f1775-151">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="f1775-151">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f1775-152">Sorgular</span><span class="sxs-lookup"><span data-stu-id="f1775-152">Queries</span></span>](index.md)
- [<span data-ttu-id="f1775-153">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="f1775-153">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="f1775-154">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="f1775-154">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="f1775-155">JOIN yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="f1775-155">Join Clause</span></span>](join-clause.md)
- [<span data-ttu-id="f1775-156">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="f1775-156">Where Clause</span></span>](where-clause.md)
- [<span data-ttu-id="f1775-157">Group by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="f1775-157">Group By Clause</span></span>](group-by-clause.md)
