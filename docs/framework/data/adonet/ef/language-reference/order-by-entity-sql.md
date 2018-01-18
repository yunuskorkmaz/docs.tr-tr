---
title: "Sipariş (varlığıyla, SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4321c5fd3f173b209d99e096ec0ebf8788437c3d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="ac8c8-102">Sipariş (varlığıyla, SQL)</span><span class="sxs-lookup"><span data-stu-id="ac8c8-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="ac8c8-103">SELECT deyimi içinde döndürülen nesne üzerinde kullanılan sıralama düzeni belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac8c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac8c8-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="ac8c8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ac8c8-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="ac8c8-106">Herhangi bir geçerli sorgu ifade bir özelliği üzerinde sıralama yapılacak belirtme.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="ac8c8-107">Birden çok sıralama ifadeleri belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="ac8c8-108">ORDER BY yan tümcesinde sıralama ifadesi dizisini sıralanmış sonuç kümesi organizasyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="ac8c8-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="ac8c8-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="ac8c8-110">Belirtilen harmanlama göre sıralama işlemi gerçekleştirilmelidir belirtir `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="ac8c8-111">COLLATE yalnızca dize ifadeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="ac8c8-112">ASC</span><span class="sxs-lookup"><span data-stu-id="ac8c8-112">ASC</span></span>  
 <span data-ttu-id="ac8c8-113">Belirtilen özellik değerleri, en yüksek değeri için en düşük değerden artan sırada sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="ac8c8-114">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-114">This is the default.</span></span>  
  
 <span data-ttu-id="ac8c8-115">DESC</span><span class="sxs-lookup"><span data-stu-id="ac8c8-115">DESC</span></span>  
 <span data-ttu-id="ac8c8-116">Belirtilen özellik değerleri, en yüksek değerden düşük değere azalan sırada sıralanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="ac8c8-117">SINIRI`n`</span><span class="sxs-lookup"><span data-stu-id="ac8c8-117">LIMIT `n`</span></span>  
 <span data-ttu-id="ac8c8-118">Yalnızca ilk `n` öğeleri seçilir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="ac8c8-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="ac8c8-119">SKIP `n`</span></span>  
 <span data-ttu-id="ac8c8-120">İlk atlar `n` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac8c8-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac8c8-121">Remarks</span></span>  
 <span data-ttu-id="ac8c8-122">ORDER BY yan tümcesi, SELECT yan tümcesi sonucuna mantıksal olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="ac8c8-123">ORDER BY yan tümcesi, select listesindeki öğeleri benzersizse kullanarak başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="ac8c8-124">ORDER BY yan tümcesi de şu anda kapsam diğer değişkenleri başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="ac8c8-125">SELECT yan tümcesi ile ayrı bir değiştirici belirtildi, ancak, ORDER BY yan tümcesi yalnızca diğer adlar from SELECT yan tümcesi başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="ac8c8-126">ORDER BY yan tümcesinde her ifade sıralı eşitsizlik (küçük veya büyük, vb.) için karşılaştırılması gereken bazı türü değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="ac8c8-127">Bu sayı, dizeleri ve tarihleri gibi genellikle skaler temelleri türleridir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="ac8c8-128">RowTypes karşılaştırılabilir türleri sıralı karşılaştırılabilir ayrıca değildir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="ac8c8-129">Kodunuzu bir sıralanmış küme üzerinde tekrarlanıyorsa dışında en üst düzey bir yansıtma için çıktı korunur, sipariş olması için kesin değildir.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  
  
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
  
 <span data-ttu-id="ac8c8-130">Sahip bir sıralı UNION, UNION ALL, EXCEPT veya INTERSECT işlemi için şu biçimi kullanın:</span><span class="sxs-lookup"><span data-stu-id="ac8c8-130">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="ac8c8-131">Sınırlı anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ac8c8-131">Restricted keywords</span></span>  
 <span data-ttu-id="ac8c8-132">Aşağıdaki anahtar sözcükler kullanıldığında tırnak içine alınmalıdır bir `ORDER BY` yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="ac8c8-132">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
-   <span data-ttu-id="ac8c8-133">ÇAPRAZ</span><span class="sxs-lookup"><span data-stu-id="ac8c8-133">CROSS</span></span>  
  
-   <span data-ttu-id="ac8c8-134">TAM</span><span class="sxs-lookup"><span data-stu-id="ac8c8-134">FULL</span></span>  
  
-   <span data-ttu-id="ac8c8-135">ANAHTARI</span><span class="sxs-lookup"><span data-stu-id="ac8c8-135">KEY</span></span>  
  
-   <span data-ttu-id="ac8c8-136">SOL</span><span class="sxs-lookup"><span data-stu-id="ac8c8-136">LEFT</span></span>  
  
-   <span data-ttu-id="ac8c8-137">SIRASI</span><span class="sxs-lookup"><span data-stu-id="ac8c8-137">ORDER</span></span>  
  
-   <span data-ttu-id="ac8c8-138">DIŞ</span><span class="sxs-lookup"><span data-stu-id="ac8c8-138">OUTER</span></span>  
  
-   <span data-ttu-id="ac8c8-139">SAĞ</span><span class="sxs-lookup"><span data-stu-id="ac8c8-139">RIGHT</span></span>  
  
-   <span data-ttu-id="ac8c8-140">SATIR</span><span class="sxs-lookup"><span data-stu-id="ac8c8-140">ROW</span></span>  
  
-   <span data-ttu-id="ac8c8-141">DEĞER</span><span class="sxs-lookup"><span data-stu-id="ac8c8-141">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="ac8c8-142">İç içe geçmiş sorgular sıralama</span><span class="sxs-lookup"><span data-stu-id="ac8c8-142">Ordering Nested Queries</span></span>  
 <span data-ttu-id="ac8c8-143">Entity Framework iç içe geçmiş bir ifade herhangi bir yere sorguda yerleştirilebilir; iç içe bir sorgu sırası korunmaz.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-143">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ac8c8-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac8c8-144">Example</span></span>  
 <span data-ttu-id="ac8c8-145">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu ORDER BY işleci bir SELECT deyiminde döndürülen nesne üzerinde kullanılan sıralama düzenini belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-145">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="ac8c8-146">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-146">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ac8c8-147">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ac8c8-147">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ac8c8-148">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ac8c8-148">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ac8c8-149">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ac8c8-149">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="ac8c8-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac8c8-150">See Also</span></span>  
 [<span data-ttu-id="ac8c8-151">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="ac8c8-151">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="ac8c8-152">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ac8c8-152">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="ac8c8-153">SKIP</span><span class="sxs-lookup"><span data-stu-id="ac8c8-153">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="ac8c8-154">LIMIT</span><span class="sxs-lookup"><span data-stu-id="ac8c8-154">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="ac8c8-155">TOP</span><span class="sxs-lookup"><span data-stu-id="ac8c8-155">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
