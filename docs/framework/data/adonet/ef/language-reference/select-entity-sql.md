---
title: "SEÇİN (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3123d76d5999d9f7201e1415d6bc4313f9767098
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="select-entity-sql"></a><span data-ttu-id="fac12-102">SEÇİN (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="fac12-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="fac12-103">Bir sorgu tarafından döndürülen öğeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="fac12-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fac12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fac12-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="fac12-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fac12-105">Arguments</span></span>  
 <span data-ttu-id="fac12-106">TÜM</span><span class="sxs-lookup"><span data-stu-id="fac12-106">ALL</span></span>  
 <span data-ttu-id="fac12-107">Çoğaltmaları sonuç kümesinde görünebilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="fac12-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="fac12-108">Tüm varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="fac12-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="fac12-109">FARKLI</span><span class="sxs-lookup"><span data-stu-id="fac12-109">DISTINCT</span></span>  
 <span data-ttu-id="fac12-110">Yalnızca benzersiz sonuçları sonuç kümesinde görünebilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="fac12-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="fac12-111">DEĞER</span><span class="sxs-lookup"><span data-stu-id="fac12-111">VALUE</span></span>  
 <span data-ttu-id="fac12-112">Yalnızca bir öğesinin belirtilmesine izin verir ve bir satır sarmalayıcı eklemez.</span><span class="sxs-lookup"><span data-stu-id="fac12-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="fac12-113">Formun sorgudan döndürülecek ilk sonuç sayısını gösterir. geçerli bir ifade `top (``expr``)`.</span><span class="sxs-lookup"><span data-stu-id="fac12-113">Any valid expression that indicates the number of first results to return from the query, of the form `top (``expr``)`.</span></span>  
  
 <span data-ttu-id="fac12-114">SINIR parametresinin [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) işleci de olanak tanır, sonuç kümesinde ilk n öğeleri seçin.</span><span class="sxs-lookup"><span data-stu-id="fac12-114">The LIMIT parameter of the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="fac12-115">Bir ifade formun:</span><span class="sxs-lookup"><span data-stu-id="fac12-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="fac12-116">`expr`olarak `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="fac12-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="fac12-117">Bir sabit değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="fac12-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fac12-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fac12-118">Remarks</span></span>  
 <span data-ttu-id="fac12-119">SELECT yan tümcesi sonra değerlendirilir [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), ve [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) yan tümceleri değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fac12-119">The SELECT clause is evaluated after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), and [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="fac12-120">SELECT yan tümcesi, yalnızca (FROM yan tümcesi, veya dış kapsamları) şu anda kapsam öğelerine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="fac12-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="fac12-121">GROUP BY yan tümcesinde belirtilen SELECT yan tümcesi yalnızca GROUP BY anahtarları için diğer adlar başvurmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fac12-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="fac12-122">FROM yan tümcesi öğelerine başvuran yalnızca toplama işlevleri içinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fac12-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="fac12-123">SELECT anahtar sözcüğü aşağıdaki bir veya daha fazla sorgu ifadeleri listesi seçim listesi olarak veya projeksiyon olarak daha resmi olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="fac12-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="fac12-124">En genel projeksiyon tek sorgu ifadesi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="fac12-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="fac12-125">Üye seçerseniz `member1` bir koleksiyondan `collection1`, tüm yeni bir koleksiyon oluşturacak `member1` her nesnenin değerleri `collection1`aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fac12-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="fac12-126">Örneğin, varsa `customers` türü koleksiyonudur `Customer` bir özellik olan `Name` türü olan `string`, seçme `Name` gelen `customers` dizeleri koleksiyonu aşağıdaki örnekte gösterildiği gibi sunacak .</span><span class="sxs-lookup"><span data-stu-id="fac12-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="fac12-127">JOIN söz dizimi (tam, iç, sol, dış, ON ve sağa) kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fac12-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="fac12-128">ON İç birleşimler için gereklidir ve nhizmetin birleştirmeler izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fac12-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="fac12-129">Satır ve değer Select yan tümceleri</span><span class="sxs-lookup"><span data-stu-id="fac12-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="fac12-130">SELECT yan tümcesi iki çeşidini destekler.</span><span class="sxs-lookup"><span data-stu-id="fac12-130"> supports two variants of the SELECT clause.</span></span> <span data-ttu-id="fac12-131">Satır seçin, ilk değişken SELECT anahtar sözcüğe göre tanımlanır ve çıkışı öngörülen bir veya daha fazla değerleri belirtmek için kullanılır. Bir satır sarmalayıcı döndürdüğü değer örtük olarak eklendiğinden, sorgu ifadesi her zaman bir çoklu küme satır sonucudur.</span><span class="sxs-lookup"><span data-stu-id="fac12-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="fac12-132">Her bir satır select sorgu ifadesinde bir diğer ad belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fac12-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="fac12-133">Diğer ad belirtilmezse,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer adı oluşturma kuralları kullanarak bir diğer ad oluşturmak çalışır.</span><span class="sxs-lookup"><span data-stu-id="fac12-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="fac12-134">Bir değer seçin, SELECT yan tümcesi türevi SELECT VALUE anahtar sözcüğü tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fac12-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="fac12-135">Belirtilmesi tek bir değer verir ve bir satır sarmalayıcı eklemez.</span><span class="sxs-lookup"><span data-stu-id="fac12-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="fac12-136">Bir satır seçin her zaman aşağıdaki örnekte gösterildiği gibi değeri seçin bakımından ifade.</span><span class="sxs-lookup"><span data-stu-id="fac12-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="fac12-137">Tüm ve ayrı değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="fac12-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="fac12-138">Her iki SELECT çeşitlemelerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BÜTÜN belirtimi izin ver veya ayrı değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="fac12-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="fac12-139">AYRI değiştiricisi belirtilirse, yinelenen sorgu ifadesi (kadar ve SELECT yan tümcesi de dahil olmak üzere) tarafından üretilen koleksiyonundan ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="fac12-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="fac12-140">Tüm değiştiricisi ise, belirtilen, Hayır yinelenen eleme gerçekleştirilir; Tüm varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="fac12-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="fac12-141">Transact-SQL farkları</span><span class="sxs-lookup"><span data-stu-id="fac12-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="fac12-142">Transact-SQL, aksine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanımını desteklemez * SELECT yan tümcesinde bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="fac12-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the * argument in the SELECT clause.</span></span>  <span data-ttu-id="fac12-143">Bunun yerine, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm kayıtları FROM yan tümcesinden koleksiyonu diğer adlar başvurarak aşağıdaki örnekte gösterildiği gibi projeye sorguları sağlar.</span><span class="sxs-lookup"><span data-stu-id="fac12-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="fac12-144">Önceki [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] sorgu ifadesi olarak ifade edilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] şu şekilde.</span><span class="sxs-lookup"><span data-stu-id="fac12-144">The previous [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="fac12-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="fac12-145">Example</span></span>  
 <span data-ttu-id="fac12-146">Aşağıdaki varlık SQL sorgusunu sorgu tarafından döndürülen öğeler belirtmek için SELECT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fac12-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="fac12-147">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="fac12-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fac12-148">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="fac12-148">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fac12-149">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="fac12-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="fac12-150">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="fac12-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="fac12-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fac12-151">See Also</span></span>  
 [<span data-ttu-id="fac12-152">Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="fac12-152">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="fac12-153">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fac12-153">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="fac12-154">SAYFANIN ÜSTÜ</span><span class="sxs-lookup"><span data-stu-id="fac12-154">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
