---
title: SİPARİş TARAFINDAN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 1233971b172079aa48227d0ec520068afbdf0952
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150075"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="bfe66-102">SİPARİş TARAFINDAN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bfe66-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="bfe66-103">SELECT deyiminde döndürülen nesnelerde kullanılan sıralama sırasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfe66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfe66-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="bfe66-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="bfe66-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="bfe66-106">Sıralamak için bir özellik belirten geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="bfe66-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="bfe66-107">Birden çok sıralama ifadeleri belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="bfe66-108">ORDER BY yan tümcesindeki tür ifadelerinin sırası, sıralanmış sonuç kümesinin organizasyonunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfe66-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="bfe66-109">HARM {collation_name}</span><span class="sxs-lookup"><span data-stu-id="bfe66-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="bfe66-110">Order BY işleminin belirtilen harmanlama göre yapılması gerektiğini `collation_name`belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="bfe66-111">COLLATE yalnızca dize ifadeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="bfe66-112">ASC</span><span class="sxs-lookup"><span data-stu-id="bfe66-112">ASC</span></span>  
 <span data-ttu-id="bfe66-113">Belirtilen özellikteki değerlerin artan sırada, en düşük değerden en yüksek değere sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="bfe66-114">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bfe66-114">This is the default.</span></span>  
  
 <span data-ttu-id="bfe66-115">DESC</span><span class="sxs-lookup"><span data-stu-id="bfe66-115">DESC</span></span>  
 <span data-ttu-id="bfe66-116">Belirtilen özellikteki değerlerin azalan sırada, en yüksek değerden en düşük değere sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="bfe66-117">Sınırı`n`</span><span class="sxs-lookup"><span data-stu-id="bfe66-117">LIMIT `n`</span></span>  
 <span data-ttu-id="bfe66-118">Yalnızca ilk `n` öğeler seçilir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="bfe66-119">Atlamak`n`</span><span class="sxs-lookup"><span data-stu-id="bfe66-119">SKIP `n`</span></span>  
 <span data-ttu-id="bfe66-120">İlk `n` öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="bfe66-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfe66-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfe66-121">Remarks</span></span>  
 <span data-ttu-id="bfe66-122">ORDER BY yan tümcesi, SELECT yan tümcesinin sonucuna mantıksal olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bfe66-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="bfe66-123">ORDER BY yan tümcesi, diğer adlarını kullanarak seçili listedeki öğelere başvuru yapabilir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="bfe66-124">ORDER BY yan tümcesi, şu anda kapsam içinde olan diğer değişkenlere de başvuruyapabilir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="bfe66-125">Ancak, SELECT yan tümcesi DISTINCT değiştirici ile belirtilmişse, ORDER BY yan tümcesi yalnızca SELECT yan tümcesi diğer adlarını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="bfe66-126">ORDER BY yan tümcesindeki her ifade, sipariş edilen eşitsizlik için karşılaştırılabilen bazı türe (daha az veya daha büyük vb.) değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bfe66-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="bfe66-127">Bu türler genellikle sayılar, dizeleri ve tarihler gibi skaler ilkel vardır.</span><span class="sxs-lookup"><span data-stu-id="bfe66-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="bfe66-128">Karşılaştırılabilir türlerin RowTypes da karşılaştırılabilir sipariş vardır.</span><span class="sxs-lookup"><span data-stu-id="bfe66-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="bfe66-129">Kodunuz, üst düzey bir projeksiyon dışında sıralı bir küme üzerinde yinelenirse, çıktının siparişinin korunduğu garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="bfe66-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="bfe66-130">Aşağıdaki örnekte, siparişin korunması garanti edilir:</span><span class="sxs-lookup"><span data-stu-id="bfe66-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="bfe66-131">Aşağıdaki sorguda, iç içe olan sorgunun sırası yoksayılır:</span><span class="sxs-lookup"><span data-stu-id="bfe66-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="bfe66-132">Sipariş edilmiş bir BİrLİk, UNION ALL, EXCEPT veya INTERSECT işlemine sahip olmak için aşağıdaki deseni kullanın:</span><span class="sxs-lookup"><span data-stu-id="bfe66-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="bfe66-133">Kısıtlı anahtar kelimeler</span><span class="sxs-lookup"><span data-stu-id="bfe66-133">Restricted keywords</span></span>  
 <span data-ttu-id="bfe66-134">Aşağıdaki anahtar kelimeler, bir `ORDER BY` yan tümcede kullanıldığında tırnak işaretlerine eklenmelidir:</span><span class="sxs-lookup"><span data-stu-id="bfe66-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="bfe66-135">Çapraz</span><span class="sxs-lookup"><span data-stu-id="bfe66-135">CROSS</span></span>  
  
- <span data-ttu-id="bfe66-136">Tam</span><span class="sxs-lookup"><span data-stu-id="bfe66-136">FULL</span></span>  
  
- <span data-ttu-id="bfe66-137">KEY</span><span class="sxs-lookup"><span data-stu-id="bfe66-137">KEY</span></span>  
  
- <span data-ttu-id="bfe66-138">LEFT</span><span class="sxs-lookup"><span data-stu-id="bfe66-138">LEFT</span></span>  
  
- <span data-ttu-id="bfe66-139">Sipariş</span><span class="sxs-lookup"><span data-stu-id="bfe66-139">ORDER</span></span>  
  
- <span data-ttu-id="bfe66-140">Dış</span><span class="sxs-lookup"><span data-stu-id="bfe66-140">OUTER</span></span>  
  
- <span data-ttu-id="bfe66-141">RIGHT</span><span class="sxs-lookup"><span data-stu-id="bfe66-141">RIGHT</span></span>  
  
- <span data-ttu-id="bfe66-142">ROW</span><span class="sxs-lookup"><span data-stu-id="bfe66-142">ROW</span></span>  
  
- <span data-ttu-id="bfe66-143">DEĞER</span><span class="sxs-lookup"><span data-stu-id="bfe66-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="bfe66-144">İç Içe Sorguları Sıralama</span><span class="sxs-lookup"><span data-stu-id="bfe66-144">Ordering Nested Queries</span></span>  
 <span data-ttu-id="bfe66-145">Varlık Çerçevesi'nde, iç içe bir ifade sorguda herhangi bir yere yerleştirilebilir; iç içe geçme sırası korunmaz.</span><span class="sxs-lookup"><span data-stu-id="bfe66-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="bfe66-146">Aşağıdaki sorgu sonuçları soyadına göre sıralar:</span><span class="sxs-lookup"><span data-stu-id="bfe66-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="bfe66-147">Aşağıdaki sorguda, iç içe olan sorgunun sırası yoksayılır:</span><span class="sxs-lookup"><span data-stu-id="bfe66-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="bfe66-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfe66-148">Example</span></span>  
 <span data-ttu-id="bfe66-149">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, SELECT deyiminde döndürülen nesnelerde kullanılan sıralama sırasını belirtmek için ORDER BY işlecikullanır.</span><span class="sxs-lookup"><span data-stu-id="bfe66-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="bfe66-150">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bfe66-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bfe66-151">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bfe66-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bfe66-152">[YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="bfe66-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bfe66-153">Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="bfe66-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="bfe66-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfe66-154">See also</span></span>

- [<span data-ttu-id="bfe66-155">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="bfe66-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="bfe66-156">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bfe66-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="bfe66-157">Atlamak</span><span class="sxs-lookup"><span data-stu-id="bfe66-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="bfe66-158">Sınırı</span><span class="sxs-lookup"><span data-stu-id="bfe66-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="bfe66-159">Sayfanın Üstü</span><span class="sxs-lookup"><span data-stu-id="bfe66-159">TOP</span></span>](top-entity-sql.md)
