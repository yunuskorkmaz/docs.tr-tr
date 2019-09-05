---
title: SıRALAMA ölçütü (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: f3310274766ff3619604e30bfb5f5ca437cb1acd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249760"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="b699c-102">SıRALAMA ölçütü (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b699c-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="b699c-103">Bir SELECT ifadesinde döndürülen nesnelerde kullanılan sıralama düzenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b699c-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b699c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b699c-104">Syntax</span></span>  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b699c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b699c-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="b699c-106">Üzerinde sıralanacak bir özellik belirten geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="b699c-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="b699c-107">Birden çok sıralama ifadesi belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b699c-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="b699c-108">ORDER BY yan tümcesindeki sıralama ifadelerinin sırası, sıralanmış sonuç kümesinin organizasyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b699c-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="b699c-109">{Collation_name} Harmanla</span><span class="sxs-lookup"><span data-stu-id="b699c-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="b699c-110">ORDER BY işleminin ' de `collation_name`belirtilen harmanlamaya göre gerçekleştirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b699c-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="b699c-111">HARMANLAMA yalnızca dize ifadeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b699c-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="b699c-112">ASC</span><span class="sxs-lookup"><span data-stu-id="b699c-112">ASC</span></span>  
 <span data-ttu-id="b699c-113">Belirtilen özelliğindeki değerlerin, en düşük değerden en yüksek değere göre artan sırada sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b699c-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="b699c-114">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b699c-114">This is the default.</span></span>  
  
 <span data-ttu-id="b699c-115">KÜMESINDE</span><span class="sxs-lookup"><span data-stu-id="b699c-115">DESC</span></span>  
 <span data-ttu-id="b699c-116">Belirtilen özelliğindeki değerlerin, en yüksek değerden en düşük değere göre azalan sırada sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b699c-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="b699c-117">SINIRLI`n`</span><span class="sxs-lookup"><span data-stu-id="b699c-117">LIMIT `n`</span></span>  
 <span data-ttu-id="b699c-118">Yalnızca ilk `n` öğeler seçilecek.</span><span class="sxs-lookup"><span data-stu-id="b699c-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="b699c-119">ŞIMDILIK`n`</span><span class="sxs-lookup"><span data-stu-id="b699c-119">SKIP `n`</span></span>  
 <span data-ttu-id="b699c-120">İlk `n` öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="b699c-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b699c-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b699c-121">Remarks</span></span>  
 <span data-ttu-id="b699c-122">ORDER BY yan tümcesi, SELECT yan tümcesinin sonucuna mantıksal olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b699c-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="b699c-123">ORDER BY yan tümcesi, seçim listesindeki öğelere diğer adlarını kullanarak başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="b699c-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="b699c-124">ORDER BY yan tümcesi, şu anda kapsamda olan diğer değişkenlere de başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="b699c-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="b699c-125">Ancak, SELECT yan tümcesi ayrı bir değiştiriciyle belirtilmişse, ORDER BY yan tümcesi yalnızca SELECT yan tümcesindeki diğer adlara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="b699c-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="b699c-126">ORDER BY yan tümcesindeki her bir ifade, sıralı eşitsizlik (küçüktür veya büyüktür, vb.) için karşılaştırılabileceğiniz bazı tür olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b699c-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="b699c-127">Bu türler genellikle sayılar, dizeler ve tarihler gibi skaler temel öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="b699c-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="b699c-128">Karşılaştırılabilir türlerin RowTypes da sıralı karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b699c-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="b699c-129">Kodunuz, üst düzey projeksiyon için dışında, sıralı bir küme üzerinde yinelenir, çıkışın sırasının korunması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="b699c-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="b699c-130">Sıralı bir UNıON, UNıON ALL, EXCEPT veya ıNTERSECT işlemine sahip olmak için aşağıdaki kalıbı kullanın:</span><span class="sxs-lookup"><span data-stu-id="b699c-130">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="b699c-131">Kısıtlanmış anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b699c-131">Restricted keywords</span></span>  
 <span data-ttu-id="b699c-132">Aşağıdaki anahtar sözcükler, bir `ORDER BY` yan tümcesinde kullanıldığında tırnak işaretleri içine alınmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b699c-132">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="b699c-133">ÜSTÜNÜ</span><span class="sxs-lookup"><span data-stu-id="b699c-133">CROSS</span></span>  
  
- <span data-ttu-id="b699c-134">TÜMÜNÜ</span><span class="sxs-lookup"><span data-stu-id="b699c-134">FULL</span></span>  
  
- <span data-ttu-id="b699c-135">KEY</span><span class="sxs-lookup"><span data-stu-id="b699c-135">KEY</span></span>  
  
- <span data-ttu-id="b699c-136">TARAFTA</span><span class="sxs-lookup"><span data-stu-id="b699c-136">LEFT</span></span>  
  
- <span data-ttu-id="b699c-137">SIPARIŞI</span><span class="sxs-lookup"><span data-stu-id="b699c-137">ORDER</span></span>  
  
- <span data-ttu-id="b699c-138">DIŞ</span><span class="sxs-lookup"><span data-stu-id="b699c-138">OUTER</span></span>  
  
- <span data-ttu-id="b699c-139">RIGHT</span><span class="sxs-lookup"><span data-stu-id="b699c-139">RIGHT</span></span>  
  
- <span data-ttu-id="b699c-140">ROW</span><span class="sxs-lookup"><span data-stu-id="b699c-140">ROW</span></span>  
  
- <span data-ttu-id="b699c-141">DEERI</span><span class="sxs-lookup"><span data-stu-id="b699c-141">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="b699c-142">Iç Içe sorguları sıralama</span><span class="sxs-lookup"><span data-stu-id="b699c-142">Ordering Nested Queries</span></span>  
 <span data-ttu-id="b699c-143">Entity Framework, iç içe geçmiş bir ifade sorgunun herhangi bir yerine yerleştirilebilir; iç içe geçmiş bir sorgunun sırası korunmaz.</span><span class="sxs-lookup"><span data-stu-id="b699c-143">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="b699c-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="b699c-144">Example</span></span>  
 <span data-ttu-id="b699c-145">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, Select ifadesinde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtmek için order by işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b699c-145">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="b699c-146">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b699c-146">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b699c-147">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b699c-147">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b699c-148">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="b699c-148">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b699c-149">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="b699c-149">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="b699c-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b699c-150">See also</span></span>

- [<span data-ttu-id="b699c-151">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="b699c-151">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="b699c-152">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b699c-152">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="b699c-153">SKIP</span><span class="sxs-lookup"><span data-stu-id="b699c-153">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="b699c-154">LIMIT</span><span class="sxs-lookup"><span data-stu-id="b699c-154">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="b699c-155">TOP</span><span class="sxs-lookup"><span data-stu-id="b699c-155">TOP</span></span>](top-entity-sql.md)
