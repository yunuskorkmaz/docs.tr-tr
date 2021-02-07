---
description: 'Daha fazla bilgi edinin: ORDER BY (Entity SQL)'
title: SıRALAMA ölçütü (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 092850e864ae95d50b615839265041a7e32b39a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696327"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="79f81-103">SıRALAMA ölçütü (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="79f81-103">ORDER BY (Entity SQL)</span></span>

<span data-ttu-id="79f81-104">Bir SELECT ifadesinde döndürülen nesnelerde kullanılan sıralama düzenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79f81-104">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79f81-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="79f81-105">Syntax</span></span>  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="79f81-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="79f81-106">Arguments</span></span>  

 `order_by_expression`  
 <span data-ttu-id="79f81-107">Üzerinde sıralanacak bir özellik belirten geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="79f81-107">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="79f81-108">Birden çok sıralama ifadesi belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="79f81-108">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="79f81-109">ORDER BY yan tümcesindeki sıralama ifadelerinin sırası, sıralanmış sonuç kümesinin organizasyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79f81-109">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="79f81-110">HARMANLAMA {collation_name}</span><span class="sxs-lookup"><span data-stu-id="79f81-110">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="79f81-111">ORDER BY işleminin ' de belirtilen harmanlamaya göre gerçekleştirilmesi gerektiğini belirtir `collation_name` .</span><span class="sxs-lookup"><span data-stu-id="79f81-111">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="79f81-112">HARMANLAMA yalnızca dize ifadeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="79f81-112">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="79f81-113">ASC</span><span class="sxs-lookup"><span data-stu-id="79f81-113">ASC</span></span>  
 <span data-ttu-id="79f81-114">Belirtilen özelliğindeki değerlerin, en düşük değerden en yüksek değere göre artan sırada sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79f81-114">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="79f81-115">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="79f81-115">This is the default.</span></span>  
  
 <span data-ttu-id="79f81-116">DESC</span><span class="sxs-lookup"><span data-stu-id="79f81-116">DESC</span></span>  
 <span data-ttu-id="79f81-117">Belirtilen özelliğindeki değerlerin, en yüksek değerden en düşük değere göre azalan sırada sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79f81-117">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="79f81-118">SıNıRLı `n`</span><span class="sxs-lookup"><span data-stu-id="79f81-118">LIMIT `n`</span></span>  
 <span data-ttu-id="79f81-119">Yalnızca ilk `n` öğeler seçilecek.</span><span class="sxs-lookup"><span data-stu-id="79f81-119">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="79f81-120">ŞIMDILIK `n`</span><span class="sxs-lookup"><span data-stu-id="79f81-120">SKIP `n`</span></span>  
 <span data-ttu-id="79f81-121">İlk öğeleri atlar `n` .</span><span class="sxs-lookup"><span data-stu-id="79f81-121">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79f81-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79f81-122">Remarks</span></span>  

 <span data-ttu-id="79f81-123">ORDER BY yan tümcesi, SELECT yan tümcesinin sonucuna mantıksal olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="79f81-123">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="79f81-124">ORDER BY yan tümcesi, seçim listesindeki öğelere diğer adlarını kullanarak başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="79f81-124">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="79f81-125">ORDER BY yan tümcesi, şu anda kapsamda olan diğer değişkenlere de başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="79f81-125">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="79f81-126">Ancak, SELECT yan tümcesi ayrı bir değiştiriciyle belirtilmişse, ORDER BY yan tümcesi yalnızca SELECT yan tümcesindeki diğer adlara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="79f81-126">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="79f81-127">ORDER BY yan tümcesindeki her bir ifade, sıralı eşitsizlik (küçüktür veya büyüktür, vb.) için karşılaştırılabileceğiniz bazı tür olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="79f81-127">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="79f81-128">Bu türler genellikle sayılar, dizeler ve tarihler gibi skaler temel öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="79f81-128">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="79f81-129">Karşılaştırılabilir türlerin RowTypes da sıralı karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="79f81-129">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="79f81-130">Kodunuz, üst düzey projeksiyon için dışında, sıralı bir küme üzerinde yinelenir, çıkışın sırasının korunması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="79f81-130">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="79f81-131">Aşağıdaki örnekte, siparişin korunması garanti edilir:</span><span class="sxs-lookup"><span data-stu-id="79f81-131">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="79f81-132">Aşağıdaki sorguda, iç içe geçmiş sorgunun sıralaması yok sayılır:</span><span class="sxs-lookup"><span data-stu-id="79f81-132">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="79f81-133">Sıralı bir UNıON, UNıON ALL, EXCEPT veya ıNTERSECT işlemine sahip olmak için aşağıdaki kalıbı kullanın:</span><span class="sxs-lookup"><span data-stu-id="79f81-133">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="79f81-134">Kısıtlanmış anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="79f81-134">Restricted keywords</span></span>  

 <span data-ttu-id="79f81-135">Aşağıdaki anahtar sözcükler, bir yan tümcesinde kullanıldığında tırnak işaretleri içine alınmalıdır `ORDER BY` :</span><span class="sxs-lookup"><span data-stu-id="79f81-135">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="79f81-136">ÜSTÜNÜ</span><span class="sxs-lookup"><span data-stu-id="79f81-136">CROSS</span></span>  
  
- <span data-ttu-id="79f81-137">TÜMÜNÜ</span><span class="sxs-lookup"><span data-stu-id="79f81-137">FULL</span></span>  
  
- <span data-ttu-id="79f81-138">KEY</span><span class="sxs-lookup"><span data-stu-id="79f81-138">KEY</span></span>  
  
- <span data-ttu-id="79f81-139">LEFT</span><span class="sxs-lookup"><span data-stu-id="79f81-139">LEFT</span></span>  
  
- <span data-ttu-id="79f81-140">SIPARIŞI</span><span class="sxs-lookup"><span data-stu-id="79f81-140">ORDER</span></span>  
  
- <span data-ttu-id="79f81-141">Dış</span><span class="sxs-lookup"><span data-stu-id="79f81-141">OUTER</span></span>  
  
- <span data-ttu-id="79f81-142">RIGHT</span><span class="sxs-lookup"><span data-stu-id="79f81-142">RIGHT</span></span>  
  
- <span data-ttu-id="79f81-143">ROW</span><span class="sxs-lookup"><span data-stu-id="79f81-143">ROW</span></span>  
  
- <span data-ttu-id="79f81-144">DEĞER</span><span class="sxs-lookup"><span data-stu-id="79f81-144">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="79f81-145">Iç Içe sorguları sıralama</span><span class="sxs-lookup"><span data-stu-id="79f81-145">Ordering Nested Queries</span></span>  

 <span data-ttu-id="79f81-146">Entity Framework, iç içe geçmiş bir ifade sorgunun herhangi bir yerine yerleştirilebilir; iç içe geçmiş bir sorgunun sırası korunmaz.</span><span class="sxs-lookup"><span data-stu-id="79f81-146">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="79f81-147">Aşağıdaki sorgu sonuçları en son ada göre sıraya alacak:</span><span class="sxs-lookup"><span data-stu-id="79f81-147">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="79f81-148">Aşağıdaki sorguda, iç içe geçmiş sorgunun sıralaması yok sayılır:</span><span class="sxs-lookup"><span data-stu-id="79f81-148">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="79f81-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="79f81-149">Example</span></span>  

 <span data-ttu-id="79f81-150">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, Select ifadesinde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtmek IÇIN order by işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="79f81-150">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="79f81-151">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="79f81-151">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="79f81-152">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="79f81-152">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="79f81-153">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="79f81-153">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="79f81-154">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="79f81-154">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="79f81-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79f81-155">See also</span></span>

- [<span data-ttu-id="79f81-156">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="79f81-156">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="79f81-157">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="79f81-157">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="79f81-158">ŞIMDILIK</span><span class="sxs-lookup"><span data-stu-id="79f81-158">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="79f81-159">SıNıRLı</span><span class="sxs-lookup"><span data-stu-id="79f81-159">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="79f81-160">Sayfanın Üstü</span><span class="sxs-lookup"><span data-stu-id="79f81-160">TOP</span></span>](top-entity-sql.md)
