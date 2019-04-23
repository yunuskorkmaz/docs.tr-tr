---
title: SEÇİN (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: d6250871b8e22b73b49a94ee7ae7835f53a7c7cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306436"
---
# <a name="select-entity-sql"></a><span data-ttu-id="64d5d-102">SEÇİN (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="64d5d-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="64d5d-103">Bir sorgu tarafından döndürülen öğeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d5d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64d5d-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="64d5d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="64d5d-105">Arguments</span></span>  
 <span data-ttu-id="64d5d-106">TÜM</span><span class="sxs-lookup"><span data-stu-id="64d5d-106">ALL</span></span>  
 <span data-ttu-id="64d5d-107">Yinelenen sonuç kümesinde göründüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="64d5d-108">Tüm varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="64d5d-109">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="64d5d-109">DISTINCT</span></span>  
 <span data-ttu-id="64d5d-110">Yalnızca benzersiz sonuçları sonuç kümesinde görünebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="64d5d-111">DEĞER</span><span class="sxs-lookup"><span data-stu-id="64d5d-111">VALUE</span></span>  
 <span data-ttu-id="64d5d-112">Yalnızca bir öğe belirtilmesine olanak sağlar ve bir satır sarmalayıcı üzerinde eklemez.</span><span class="sxs-lookup"><span data-stu-id="64d5d-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="64d5d-113">Form sorgudan döndürülecek ilk sonuç sayısını gösteren herhangi bir geçerli ifade `top(expr)`.</span><span class="sxs-lookup"><span data-stu-id="64d5d-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="64d5d-114">SINIRI parametresi [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) işleci de olanak tanır, sonuç kümesindeki ilk n öğe seçin.</span><span class="sxs-lookup"><span data-stu-id="64d5d-114">The LIMIT parameter of the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="64d5d-115">Bir ifade formun:</span><span class="sxs-lookup"><span data-stu-id="64d5d-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="64d5d-116">`expr` as `identifier` &#124; `expr`</span><span class="sxs-lookup"><span data-stu-id="64d5d-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="64d5d-117">Değişmez değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="64d5d-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64d5d-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64d5d-118">Remarks</span></span>  
 <span data-ttu-id="64d5d-119">SELECT yan tümcesi sonra değerlendirilir [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), ve [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) yan tümceleri değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-119">The SELECT clause is evaluated after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), and [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="64d5d-120">SELECT yan tümcesi yalnızca (FROM yan tümcesi, veya dış kapsamları) şu anda kapsam öğelerine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="64d5d-121">GROUP BY yan tümcesi belirtilmiş ise SELECT yan tümcesi yalnızca GROUP BY anahtarları için diğer adlar başvurmak için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="64d5d-122">FROM yan tümcesi öğelerine başvuran yalnızca toplama işlevlerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="64d5d-123">SELECT anahtar sözcüğünü izleyen bir veya daha fazla sorgu ifadeleri listesini seçim listesi olarak veya daha eski adıyla projeksiyon olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="64d5d-124">En genel projeksiyon tek sorgu ifadesi biçimindedir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="64d5d-125">Bir üye seçtiğinizde `member1` bir koleksiyondan `collection1`, tüm yeni bir koleksiyon oluşturacak `member1` her nesne için değerler `collection1`aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="64d5d-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="64d5d-126">Örneğin, varsa `customers` türü koleksiyonudur `Customer` bir özelliği olan `Name` türü olan `string`u seçerek `Name` gelen `customers` dizelerden oluşan bir koleksiyonu, aşağıdaki örnekte gösterildiği gibi verecek olan .</span><span class="sxs-lookup"><span data-stu-id="64d5d-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="64d5d-127">JOIN söz dizimini (tam, iç, sol, dış, ON ve SAĞDA) kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="64d5d-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="64d5d-128">Şirket iç birleştirmeler için gereklidir ve nBaşka birleştirmeler izin verilir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="64d5d-129">Yan tümceleri satır ve değer seçin</span><span class="sxs-lookup"><span data-stu-id="64d5d-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="64d5d-130">SELECT yan tümcesi birinin iki çeşidi destekler.</span><span class="sxs-lookup"><span data-stu-id="64d5d-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="64d5d-131">İlk satırı seçin, değişken, SELECT anahtar sözcüğü tarafından tanımlanır ve çıkış öngörülen bir veya daha fazla değerleri belirtmek için kullanılabilir. Bir satır sarmalayıcı döndürülen değerlerden örtük olarak eklendiğinden, sorgu ifadesi her zaman bir çoklu küme satır sonucudur.</span><span class="sxs-lookup"><span data-stu-id="64d5d-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="64d5d-132">Her sorgu ifadesi içinde bir satırı seçin, bir diğer ad belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="64d5d-133">Diğer ad yok belirtilirse,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer ad oluşturma kurallarını kullanarak bir diğer ad oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="64d5d-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="64d5d-134">Bir değişken değeri select, SELECT yan tümcesi, SELECT VALUE anahtar sözcüğü tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="64d5d-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="64d5d-135">Yalnızca bir değer belirtilmesine olanak tanır ve satır sarmalayıcı eklemez.</span><span class="sxs-lookup"><span data-stu-id="64d5d-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="64d5d-136">Bir satır seçin her zaman aşağıdaki örnekte gösterildiği gibi değeri seçin açısından ifade.</span><span class="sxs-lookup"><span data-stu-id="64d5d-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="64d5d-137">Tüm ve ayrı değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="64d5d-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="64d5d-138">Her iki SELECT türevleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BÜTÜN belirtilmesine izin ver veya ayrı değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="64d5d-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="64d5d-139">FARKLI değiştiricisi belirtilirse, çoğaltmaları (en fazla ve SELECT yan tümcesi dahil olmak üzere) sorgu ifadesi tarafından üretilen koleksiyondan ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="64d5d-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="64d5d-140">Belirtilen, Hayır yinelenen tüm değiştiricisi, eleme gerçekleştirilir; Tüm varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="64d5d-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="64d5d-141">Transact-SQL arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="64d5d-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="64d5d-142">Transact-SQL, aksine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanımını desteklemiyor \* SELECT yan tümcesinde bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="64d5d-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="64d5d-143">Bunun yerine, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm kayıtları süzer koleksiyonu diğer adlar FROM yan tümcesinden başvurarak aşağıdaki örnekte gösterildiği gibi projeye sorguları sağlar.</span><span class="sxs-lookup"><span data-stu-id="64d5d-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="64d5d-144">Önceki [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] sorgu ifadesi olarak ifade edilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] şu şekilde.</span><span class="sxs-lookup"><span data-stu-id="64d5d-144">The previous [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="64d5d-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="64d5d-145">Example</span></span>  
 <span data-ttu-id="64d5d-146">Aşağıdaki varlık SQL sorgusu seçme işleci bir sorgu tarafından döndürülen öğeleri belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="64d5d-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="64d5d-147">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="64d5d-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="64d5d-148">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="64d5d-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="64d5d-149">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="64d5d-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="64d5d-150">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="64d5d-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="64d5d-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64d5d-151">See also</span></span>

- [<span data-ttu-id="64d5d-152">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="64d5d-152">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [<span data-ttu-id="64d5d-153">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="64d5d-153">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="64d5d-154">TOP</span><span class="sxs-lookup"><span data-stu-id="64d5d-154">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
