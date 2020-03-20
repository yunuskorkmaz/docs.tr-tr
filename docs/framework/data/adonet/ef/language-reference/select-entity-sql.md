---
title: SELECT (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: de6c497e7d781d705c68092e4a13ee07b727b2b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149915"
---
# <a name="select-entity-sql"></a><span data-ttu-id="9eca4-102">SELECT (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="9eca4-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="9eca4-103">Sorgu tarafından döndürülen öğeleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eca4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9eca4-104">Syntax</span></span>  
  
```sql  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
-- or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="9eca4-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="9eca4-105">Arguments</span></span>  
 <span data-ttu-id="9eca4-106">TÜMÜ</span><span class="sxs-lookup"><span data-stu-id="9eca4-106">ALL</span></span>  
 <span data-ttu-id="9eca4-107">Sonuç kümesinde yinelemelerin görünebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="9eca4-108">ALL varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9eca4-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="9eca4-109">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="9eca4-109">DISTINCT</span></span>  
 <span data-ttu-id="9eca4-110">Sonuç kümesinde yalnızca benzersiz sonuçların görünebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="9eca4-111">DEĞER</span><span class="sxs-lookup"><span data-stu-id="9eca4-111">VALUE</span></span>  
 <span data-ttu-id="9eca4-112">Yalnızca bir öğenin belirtilmesine izin verir ve satır sarıcıya eklemez.</span><span class="sxs-lookup"><span data-stu-id="9eca4-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="9eca4-113">Formun `top(expr)`sorgudan döndürülecek ilk sonuç sayısını gösteren geçerli bir ifade .</span><span class="sxs-lookup"><span data-stu-id="9eca4-113">Any valid expression that indicates the number of first results to return from the query, of the form `top(expr)`.</span></span>  
  
 <span data-ttu-id="9eca4-114">[ORDER BY](order-by-entity-sql.md) işlecinin LIMIT parametresi, sonuç kümesindeki ilk n maddelerini seçmenize de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9eca4-114">The LIMIT parameter of the [ORDER BY](order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="9eca4-115">Formun bir ifadesi:</span><span class="sxs-lookup"><span data-stu-id="9eca4-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="9eca4-116">`expr`olarak `identifier` &#124;`expr`</span><span class="sxs-lookup"><span data-stu-id="9eca4-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="9eca4-117">Gerçek bir ifade ya da ifade.</span><span class="sxs-lookup"><span data-stu-id="9eca4-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eca4-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9eca4-118">Remarks</span></span>  
 <span data-ttu-id="9eca4-119">SELECT yan tümcesi [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md)ve [HAVING](having-entity-sql.md) yan tümceleri değerlendirildikten sonra değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-119">The SELECT clause is evaluated after the [FROM](from-entity-sql.md), [GROUP BY](group-by-entity-sql.md), and [HAVING](having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="9eca4-120">SELECT yan tümcesi yalnızca şu anda kapsam içinde olan (FROM yan tümcesinden veya dış kapsamlardan) maddelere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="9eca4-121">GROUP BY yan tümcesi belirtilmişse, SELECT yan tümcesinin yalnızca GROUP BY tuşlarına başvurmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="9eca4-122">FROM yan tümcesi öğelerine atıfta bulunulması yalnızca toplu işlevlerde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="9eca4-123">SELECT anahtar sözcükten sonra bir veya daha fazla sorgu ifadesinin listesi seçlistesi veya daha resmi olarak projeksiyon olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="9eca4-124">Projeksiyonun en genel biçimi tek bir sorgu ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="9eca4-125">`member1` Bir koleksiyondan `collection1`bir üye seçerseniz, aşağıdaki örnekte `member1` gösterildiği `collection1`gibi, her nesne için tüm değerlerin yeni bir koleksiyon üretecektir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```sql  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="9eca4-126">Örneğin, türünde `customers` `Customer` `Name` `string`bir özelliğe sahip bir tür koleksiyonu ise, aşağıdaki örnekte gösterildiği gibi, seçerek `Name` dizeleri bir koleksiyon `customers` verecektir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```sql  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="9eca4-127">JOIN sözdizimini (TAM, İç, SOL, DıŞ, AVEVek) ve SAĞ olarak da kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9eca4-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="9eca4-128">ON iç birleştirmeler için gereklidir ve çapraz birleştirmeler için nto izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="9eca4-129">Satır ve Değer Seç Yan Tümceleri</span><span class="sxs-lookup"><span data-stu-id="9eca4-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="9eca4-130">SELECT yan tümcesinin iki türevlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="9eca4-130">supports two variants of the SELECT clause.</span></span> <span data-ttu-id="9eca4-131">İlk varyant, satır seç, SELECT anahtar sözcüğü tarafından tanımlanır ve öngörenebilmek gereken bir veya daha fazla değer belirtmek için kullanılabilir. Satır sarıcı döndürülen değerlerin etrafına örtülü olarak eklenmiştir, sorgu ifadesinin sonucu her zaman bir satır çok kümesidir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="9eca4-132">Bir satırdaki her sorgu ifadesi nin bir takma ad belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="9eca4-133">Takma ad belirtilmemişse,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] diğer ad oluşturma kurallarını kullanarak bir takma ad oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="9eca4-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="9eca4-134">SELECT yan tümcesinin diğer varyantı, değer seçin, SELECT VALUE anahtar kelimesi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9eca4-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="9eca4-135">Yalnızca bir değerin belirtilmesine izin verir ve satır sarıcı eklemez.</span><span class="sxs-lookup"><span data-stu-id="9eca4-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="9eca4-136">Aşağıdaki örnekte gösterildiği gibi, bir satır seçimi, VALUE SELECT açısından her zaman ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```sql  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="9eca4-137">Tüm ve Farklı Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="9eca4-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="9eca4-138">SELECT'in her [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iki varyantı da BIR ALL veya DISTINCT değiştiricinin belirtimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="9eca4-139">DISTINCT değiştirici belirtilirse, yinelenenler sorgu ifadesi tarafından üretilen koleksiyondan (SELECT yan tümcesi dahil) ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="9eca4-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="9eca4-140">TÜM değiştirici belirtilirse, yinelenen eleme yapılmaz; ALL varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9eca4-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="9eca4-141">Transact-SQL'den Farklar</span><span class="sxs-lookup"><span data-stu-id="9eca4-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="9eca4-142">Transact-SQL'in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aksine, SELECT yan tümcesindeki \* bağımsız değişkeninin kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9eca4-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the \* argument in the SELECT clause.</span></span>  <span data-ttu-id="9eca4-143">Bunun [!INCLUDE[esql](../../../../../../includes/esql-md.md)] yerine, aşağıdaki örnekte gösterildiği gibi, FROM yan tümcesinden toplama takma adlarına başvurarak sorguların tüm kayıtları yansıtmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9eca4-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```sql  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="9eca4-144">Önceki Transact-SQL sorgu ifadesi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki şekilde ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="9eca4-144">The previous Transact-SQL query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```sql  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="9eca4-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="9eca4-145">Example</span></span>  
 <span data-ttu-id="9eca4-146">Aşağıdaki Entity SQL sorgusu, sorgu tarafından döndürülecek öğeleri belirtmek için SELECT işleci kullanır.</span><span class="sxs-lookup"><span data-stu-id="9eca4-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="9eca4-147">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9eca4-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9eca4-148">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9eca4-148">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9eca4-149">[YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="9eca4-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9eca4-150">Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="9eca4-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="9eca4-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9eca4-151">See also</span></span>

- [<span data-ttu-id="9eca4-152">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="9eca4-152">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="9eca4-153">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9eca4-153">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="9eca4-154">Sayfanın Üstü</span><span class="sxs-lookup"><span data-stu-id="9eca4-154">TOP</span></span>](top-entity-sql.md)
