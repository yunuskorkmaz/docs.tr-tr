---
title: Seç (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 3d3564c37d8971d3261cb47acb774bd1b9f92192
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249210"
---
# <a name="select-entity-sql"></a><span data-ttu-id="58559-102">Seç (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="58559-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="58559-103">Bir sorgu tarafından döndürülen öğeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="58559-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58559-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58559-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="58559-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="58559-105">Arguments</span></span>  
 <span data-ttu-id="58559-106">BÜTÜN</span><span class="sxs-lookup"><span data-stu-id="58559-106">ALL</span></span>  
 <span data-ttu-id="58559-107">Tekrarların sonuç kümesinde görünebilen belirtir.</span><span class="sxs-lookup"><span data-stu-id="58559-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="58559-108">TÜMÜ varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="58559-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="58559-109">AYRI</span><span class="sxs-lookup"><span data-stu-id="58559-109">DISTINCT</span></span>  
 <span data-ttu-id="58559-110">Sonuç kümesinde yalnızca benzersiz sonuçların görüneabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="58559-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="58559-111">DEERI</span><span class="sxs-lookup"><span data-stu-id="58559-111">VALUE</span></span>  
 <span data-ttu-id="58559-112">Yalnızca bir öğenin belirtilmesini sağlar ve satır sarmalayıcısı eklemez.</span><span class="sxs-lookup"><span data-stu-id="58559-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="58559-113">Formun `top(expr)`sorgusundan döndürülecek ilk sonuçların sayısını gösteren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="58559-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="58559-114">[Order by](order-by-entity-sql.md) işlecinin LIMIT parametresi, sonuç kümesindeki ilk n öğeyi seçmenizi de sağlar.</span><span class="sxs-lookup"><span data-stu-id="58559-114">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="58559-115">Formun bir ifadesi:</span><span class="sxs-lookup"><span data-stu-id="58559-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="58559-116">`expr`as `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="58559-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="58559-117">Bir sabit değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="58559-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58559-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58559-118">Remarks</span></span>  
 <span data-ttu-id="58559-119">SELECT yan tümcesi from, [Group By](group-by-entity-sql.md)ve [HAVING](having-entity-sql.md) yan [tümcelerinden](from-entity-sql.md)sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="58559-119">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="58559-120">SELECT yan tümcesi yalnızca şu anda kapsamda olan öğelere (FROM yan tümcesinden veya dış kapsamlardan) başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="58559-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="58559-121">GROUP BY yan tümcesi belirtilmişse, SELECT yan tümcesinin yalnızca GROUP BY anahtarlarına yönelik diğer adlara başvuruda bulunmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="58559-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="58559-122">FROM yan tümcesi öğelerine başvurmak için yalnızca toplama işlevlerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="58559-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="58559-123">SELECT anahtar sözcüğünü izleyen bir veya daha fazla sorgu ifadesinin listesi, seçim listesi veya yansıtma olarak daha resmi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="58559-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="58559-124">En genel projeksiyon formu tek bir sorgu deyimidir.</span><span class="sxs-lookup"><span data-stu-id="58559-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="58559-125">`member1` Bir koleksiyondan `collection1`üye seçerseniz, aşağıdaki örnekte gösterildiği gibi, içindeki `collection1`her bir nesne için tüm `member1` değerlerin yeni bir koleksiyonunu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="58559-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="58559-126">Örneğin, `customers` türünde `Name` `Customer` `Name` bir özelliğine sahip olan bir tür koleksiyonudur, öğesinden `customers` seçim aşağıdaki örnekte gösterildiği gibi bir dize koleksiyonu olur. `string` .</span><span class="sxs-lookup"><span data-stu-id="58559-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="58559-127">BIRLEŞIM söz dizimini (tam, Iç, sol, dış, açık ve sağ) kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="58559-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="58559-128">ON, İç birleştirmeler için gereklidir ve buna Çapraz birleştirmeler için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="58559-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="58559-129">Satır ve değer seçim yan tümceleri</span><span class="sxs-lookup"><span data-stu-id="58559-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="58559-130">SELECT yan tümcesinin iki çeşidini destekler.</span><span class="sxs-lookup"><span data-stu-id="58559-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="58559-131">İlk varyant, Row Select, SELECT anahtar sözcüğü tarafından tanımlanır ve, yansıtılmalıdır bir veya daha fazla değer belirtmek için kullanılabilir. Satır sarmalayıcı döndürülen değerlerin çevresine örtük olarak eklendiğinden, sorgu ifadesinin sonucu her zaman bir satır kümesi olur.</span><span class="sxs-lookup"><span data-stu-id="58559-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="58559-132">Satırdaki her sorgu ifadesi Select bir diğer ad belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="58559-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="58559-133">Diğer ad belirtilmemişse,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer ad oluşturma kurallarını kullanarak bir diğer ad oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="58559-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="58559-134">SELECT yan tümcesinin diğer varyantı, değer Select, SELECT VALUE anahtar sözcüğü tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="58559-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="58559-135">Yalnızca bir değerin belirtilmesini sağlar ve bir satır sarmalayıcı eklemez.</span><span class="sxs-lookup"><span data-stu-id="58559-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="58559-136">Aşağıdaki örnekte gösterildiği gibi, bir satır seçimi her zaman değer SEÇIM bakımından ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="58559-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="58559-137">Tüm ve farklı değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="58559-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="58559-138">' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] In her iki varyantı de tüm veya ayrı bir değiştirici belirtimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="58559-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="58559-139">AYRı değiştirici belirtilirse, yinelemeler sorgu ifadesi tarafından üretilen koleksiyondan kaldırılır (SELECT yan tümcesi ile ve dahil).</span><span class="sxs-lookup"><span data-stu-id="58559-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="58559-140">Tüm değiştirici belirtilirse, yinelenen bir eleme gerçekleştirilmez; TÜMÜ varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="58559-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="58559-141">Transact-SQL arasındaki farklılıklar</span><span class="sxs-lookup"><span data-stu-id="58559-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="58559-142">Transact-SQL ' den [!INCLUDE[esql](../../../../../../includes/esql-md.md)] farklı olarak, select yan tümcesinde \* bağımsız değişkeninin kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="58559-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="58559-143">Bunun yerine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aşağıdaki örnekte gösterildiği gibi,, from yan tümcesindeki koleksiyon diğer adlarına başvurarak tüm kayıtları proje için sorgular sağlar.</span><span class="sxs-lookup"><span data-stu-id="58559-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="58559-144">Önceki Transact-SQL sorgu ifadesi aşağıdaki şekilde ifade [!INCLUDE[esql](../../../../../../includes/esql-md.md)] edilir.</span><span class="sxs-lookup"><span data-stu-id="58559-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="58559-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="58559-145">Example</span></span>  
 <span data-ttu-id="58559-146">Aşağıdaki Entity SQL sorgusu, bir sorgu tarafından döndürülecek öğeleri belirtmek için SELECT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="58559-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="58559-147">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="58559-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="58559-148">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="58559-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="58559-149">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="58559-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="58559-150">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="58559-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="58559-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58559-151">See also</span></span>

- [<span data-ttu-id="58559-152">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="58559-152">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="58559-153">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="58559-153">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="58559-154">TOP</span><span class="sxs-lookup"><span data-stu-id="58559-154">TOP</span></span>](top-entity-sql.md)
