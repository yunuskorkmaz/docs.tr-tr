---
title: SıRALAMA ölçütü (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 2010ef9d6fe37e65824cac877074453db1b789db
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319440"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="bc8d8-102">SıRALAMA ölçütü (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bc8d8-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="bc8d8-103">Bir SELECT ifadesinde döndürülen nesnelerde kullanılan sıralama düzenini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc8d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc8d8-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="bc8d8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bc8d8-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="bc8d8-106">Üzerinde sıralanacak bir özellik belirten geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="bc8d8-107">Birden çok sıralama ifadesi belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="bc8d8-108">ORDER BY yan tümcesindeki sıralama ifadelerinin sırası, sıralanmış sonuç kümesinin organizasyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="bc8d8-109">{Collation_name} Harmanla</span><span class="sxs-lookup"><span data-stu-id="bc8d8-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="bc8d8-110">ORDER BY işleminin `collation_name` ' da belirtilen harmanlamaya göre gerçekleştirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="bc8d8-111">HARMANLAMA yalnızca dize ifadeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="bc8d8-112">ASC</span><span class="sxs-lookup"><span data-stu-id="bc8d8-112">ASC</span></span>  
 <span data-ttu-id="bc8d8-113">Belirtilen özelliğindeki değerlerin, en düşük değerden en yüksek değere göre artan sırada sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="bc8d8-114">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-114">This is the default.</span></span>  
  
 <span data-ttu-id="bc8d8-115">KÜMESINDE</span><span class="sxs-lookup"><span data-stu-id="bc8d8-115">DESC</span></span>  
 <span data-ttu-id="bc8d8-116">Belirtilen özelliğindeki değerlerin, en yüksek değerden en düşük değere göre azalan sırada sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="bc8d8-117">SıNıR `n`</span><span class="sxs-lookup"><span data-stu-id="bc8d8-117">LIMIT `n`</span></span>  
 <span data-ttu-id="bc8d8-118">Yalnızca ilk `n` öğe seçilecek.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="bc8d8-119">Atla `n`</span><span class="sxs-lookup"><span data-stu-id="bc8d8-119">SKIP `n`</span></span>  
 <span data-ttu-id="bc8d8-120">İlk @no__t 0 öğeyi atlar.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc8d8-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc8d8-121">Remarks</span></span>  
 <span data-ttu-id="bc8d8-122">ORDER BY yan tümcesi, SELECT yan tümcesinin sonucuna mantıksal olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="bc8d8-123">ORDER BY yan tümcesi, seçim listesindeki öğelere diğer adlarını kullanarak başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="bc8d8-124">ORDER BY yan tümcesi, şu anda kapsamda olan diğer değişkenlere de başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="bc8d8-125">Ancak, SELECT yan tümcesi ayrı bir değiştiriciyle belirtilmişse, ORDER BY yan tümcesi yalnızca SELECT yan tümcesindeki diğer adlara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="bc8d8-126">ORDER BY yan tümcesindeki her bir ifade, sıralı eşitsizlik (küçüktür veya büyüktür, vb.) için karşılaştırılabileceğiniz bazı tür olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="bc8d8-127">Bu türler genellikle sayılar, dizeler ve tarihler gibi skaler temel öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="bc8d8-128">Karşılaştırılabilir türlerin RowTypes da sıralı karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="bc8d8-129">Kodunuz, üst düzey projeksiyon için dışında, sıralı bir küme üzerinde yinelenir, çıkışın sırasının korunması garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="bc8d8-130">Aşağıdaki örnekte, siparişin korunması garanti edilir:</span><span class="sxs-lookup"><span data-stu-id="bc8d8-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="bc8d8-131">Aşağıdaki sorguda, iç içe geçmiş sorgunun sıralaması yok sayılır:</span><span class="sxs-lookup"><span data-stu-id="bc8d8-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="bc8d8-132">Sıralı bir UNıON, UNıON ALL, EXCEPT veya ıNTERSECT işlemine sahip olmak için aşağıdaki kalıbı kullanın:</span><span class="sxs-lookup"><span data-stu-id="bc8d8-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="bc8d8-133">Kısıtlanmış anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="bc8d8-133">Restricted keywords</span></span>  
 <span data-ttu-id="bc8d8-134">Aşağıdaki anahtar sözcükler `ORDER BY` yan tümcesinde kullanıldığında tırnak işaretleri içine alınmalıdır:</span><span class="sxs-lookup"><span data-stu-id="bc8d8-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="bc8d8-135">ÜSTÜNÜ</span><span class="sxs-lookup"><span data-stu-id="bc8d8-135">CROSS</span></span>  
  
- <span data-ttu-id="bc8d8-136">TÜMÜNÜ</span><span class="sxs-lookup"><span data-stu-id="bc8d8-136">FULL</span></span>  
  
- <span data-ttu-id="bc8d8-137">KEY</span><span class="sxs-lookup"><span data-stu-id="bc8d8-137">KEY</span></span>  
  
- <span data-ttu-id="bc8d8-138">TARAFTA</span><span class="sxs-lookup"><span data-stu-id="bc8d8-138">LEFT</span></span>  
  
- <span data-ttu-id="bc8d8-139">SIPARIŞI</span><span class="sxs-lookup"><span data-stu-id="bc8d8-139">ORDER</span></span>  
  
- <span data-ttu-id="bc8d8-140">Dış</span><span class="sxs-lookup"><span data-stu-id="bc8d8-140">OUTER</span></span>  
  
- <span data-ttu-id="bc8d8-141">RIGHT</span><span class="sxs-lookup"><span data-stu-id="bc8d8-141">RIGHT</span></span>  
  
- <span data-ttu-id="bc8d8-142">ROW</span><span class="sxs-lookup"><span data-stu-id="bc8d8-142">ROW</span></span>  
  
- <span data-ttu-id="bc8d8-143">DEERI</span><span class="sxs-lookup"><span data-stu-id="bc8d8-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="bc8d8-144">Iç Içe sorguları sıralama</span><span class="sxs-lookup"><span data-stu-id="bc8d8-144">Ordering Nested Queries</span></span>  
 <span data-ttu-id="bc8d8-145">Entity Framework, iç içe geçmiş bir ifade sorgunun herhangi bir yerine yerleştirilebilir; iç içe geçmiş bir sorgunun sırası korunmaz.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="bc8d8-146">Aşağıdaki sorgu sonuçları en son ada göre sıraya alacak:</span><span class="sxs-lookup"><span data-stu-id="bc8d8-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="bc8d8-147">Aşağıdaki sorguda, iç içe geçmiş sorgunun sıralaması yok sayılır:</span><span class="sxs-lookup"><span data-stu-id="bc8d8-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="bc8d8-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc8d8-148">Example</span></span>  
 <span data-ttu-id="bc8d8-149">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusu, SELECT ifadesinde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtmek için ORDER BY işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="bc8d8-150">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bc8d8-151">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bc8d8-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bc8d8-152">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bc8d8-153">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="bc8d8-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="bc8d8-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc8d8-154">See also</span></span>

- [<span data-ttu-id="bc8d8-155">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="bc8d8-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="bc8d8-156">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bc8d8-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="bc8d8-157">SKIP</span><span class="sxs-lookup"><span data-stu-id="bc8d8-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="bc8d8-158">LIMIT</span><span class="sxs-lookup"><span data-stu-id="bc8d8-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="bc8d8-159">TOP</span><span class="sxs-lookup"><span data-stu-id="bc8d8-159">TOP</span></span>](top-entity-sql.md)
