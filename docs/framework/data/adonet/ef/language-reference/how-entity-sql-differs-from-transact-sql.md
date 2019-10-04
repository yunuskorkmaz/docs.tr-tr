---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e0af0a415d812337d6abf449e9ee170526c3df0c
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833716"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="c5524-102">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="c5524-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="c5524-103">Bu konuda [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ve Transact-SQL arasındaki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5524-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="c5524-104">Devralma ve Ilişkiler desteği</span><span class="sxs-lookup"><span data-stu-id="c5524-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-105">doğrudan kavramsal varlık şemaları ile çalışarak devralma ve ilişkiler gibi kavramsal model özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="c5524-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="c5524-106">Devralmayla çalışırken, genellikle bir üst tür alt türünün örneklerini seçmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5524-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="c5524-107">@No__t-1 ' deki [OfType](oftype-entity-sql.md) işleci (`oftype` ' de diziler C# içinde) bu yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5524-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="c5524-108">Koleksiyonlar için destek</span><span class="sxs-lookup"><span data-stu-id="c5524-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-109">, koleksiyonları birinci sınıf varlıklar olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c5524-109">treats collections as first-class entities.</span></span> <span data-ttu-id="c5524-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c5524-110">For example:</span></span>  
  
- <span data-ttu-id="c5524-111">Koleksiyon ifadeleri `from` yan tümcesinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c5524-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="c5524-112">`in` ve `exists` alt sorguları tüm koleksiyonlara izin verecek şekilde genelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c5524-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="c5524-113">Alt sorgu tek bir koleksiyon türüdür.</span><span class="sxs-lookup"><span data-stu-id="c5524-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="c5524-114">`e1 in e2` ve `exists(e)`, bu işlemleri gerçekleştirecek @no__t 2 yapılarıdır.</span><span class="sxs-lookup"><span data-stu-id="c5524-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="c5524-115">@No__t-0, `intersect` ve `except` gibi işlemleri ayarlayın, artık koleksiyonlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="c5524-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="c5524-116">Birleşimler koleksiyonlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="c5524-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="c5524-117">Ifadeler için destek</span><span class="sxs-lookup"><span data-stu-id="c5524-117">Support for Expressions</span></span>  
 <span data-ttu-id="c5524-118">Transact-SQL 'de alt sorgular (tablolar) ve ifadeler (satırlar ve sütunlar) vardır.</span><span class="sxs-lookup"><span data-stu-id="c5524-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="c5524-119">Koleksiyonları ve iç içe koleksiyonları desteklemek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] her şeyi bir ifadeye getirir.</span><span class="sxs-lookup"><span data-stu-id="c5524-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-120">Transact-SQL ' den daha birleştirilebilir — her ifade her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5524-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="c5524-121">Sorgu ifadeleri her zaman öngörülen türlerin koleksiyonlarına neden olur ve koleksiyon ifadesine izin verildiğinde her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5524-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="c5524-122">@No__t-0 ' da desteklenmeyen Transact-SQL ifadeleri hakkında daha fazla bilgi için bkz. [Desteklenmeyen ifadeler](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c5524-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c5524-123">Tüm geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c5524-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="c5524-124">Alt sorguları Tekdüzen olarak Işleme</span><span class="sxs-lookup"><span data-stu-id="c5524-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="c5524-125">Tablo üzerinde vurgusu verildiğine göre Transact-SQL, alt sorgular için bağlama yorumu uygular.</span><span class="sxs-lookup"><span data-stu-id="c5524-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="c5524-126">Örneğin, `from` yan tümcesindeki bir alt sorgu bir çoklu küme (tablo) olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c5524-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="c5524-127">Ancak `select` yan tümcesinde kullanılan alt sorgu, skaler bir alt sorgu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c5524-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="c5524-128">Benzer şekilde, bir `in` işlecinin sol tarafında kullanılan bir alt sorgu skaler bir alt sorgu olarak değerlendirilir ve sağ taraftaki bir çoklu küme alt sorgusu olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="c5524-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-129">bu farklılıkları ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c5524-129">eliminates these differences.</span></span> <span data-ttu-id="c5524-130">Bir ifade, kullanıldığı bağlama bağlı olmayan bir Tekdüzen yorumu içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c5524-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-131">tüm alt sorguları çoklu küme alt sorguları olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c5524-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="c5524-132">Alt sorgudan skaler bir değer isteniyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir koleksiyon üzerinde çalışan `anyelement` işleci sağlar (Bu durumda alt sorgu) ve koleksiyondan tek bir değer ayıklar.</span><span class="sxs-lookup"><span data-stu-id="c5524-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="c5524-133">Alt sorgular için örtük zorlamalar önleme</span><span class="sxs-lookup"><span data-stu-id="c5524-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="c5524-134">Tek biçimli alt sorgular için ilgili bir yan etkisi, alt sorguları skaler değerlere örtülü olarak dönüştürmedir.</span><span class="sxs-lookup"><span data-stu-id="c5524-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="c5524-135">Özellikle Transact-SQL ' de bir dizi çoklu küme (tek bir alan ile), veri türü alanın bulunduğu bir skalar değere örtülü olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="c5524-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-136">bu örtük zorlama 'yi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c5524-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-137">, bir koleksiyondaki tek bir değeri ayıklamak için ANYELEMENT işlecini ve sorgu ifadesi sırasında satır sarmalayıcı oluşturulmasını önlemek için bir `select value` yan tümcesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5524-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="c5524-138">Değer seçin: örtük satır sarmalayıcısı ' ı önleme</span><span class="sxs-lookup"><span data-stu-id="c5524-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="c5524-139">Bir Transact-SQL alt sorgusunda SELECT yan tümcesi, yan tümcesindeki öğelerin etrafında örtük olarak bir satır sarmalayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c5524-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="c5524-140">Bu, yapı veya nesne koleksiyonları oluşturduğumuz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c5524-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="c5524-141">Transact-SQL, tek bir alanla RowType ve aynı veri türünde tek bir değer arasında örtük bir zorlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5524-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-142">, örtük satır oluşturmayı atlamak için `select value` yan tümcesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5524-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="c5524-143">@No__t-0 yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5524-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="c5524-144">Böyle bir yan tümce kullanıldığında, `select` yan tümcesindeki öğelerin çevresine satır sarmalayıcı oluşturulmadı ve istenen şeklin bir koleksiyonu üretile, örneğin: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="c5524-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-145">Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5524-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="c5524-146">`select`, projeksiyondaki bir veya daha fazla öğeyi alır ve alanları içeren bir veri kaydına aşağıdaki şekilde neden olur:</span><span class="sxs-lookup"><span data-stu-id="c5524-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="c5524-147">Sol bağıntı ve diğer ad</span><span class="sxs-lookup"><span data-stu-id="c5524-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="c5524-148">Transact-SQL içinde, belirli bir kapsamdaki ifadeler (`select` veya `from` gibi tek bir yan tümce), aynı kapsamda daha önce tanımlanan ifadelere başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="c5524-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="c5524-149">SQL 'in bazı diatıtılarını (Transact-SQL dahil) `from` yan tümcesinde bunlarla sınırlı biçimleri destekler.</span><span class="sxs-lookup"><span data-stu-id="c5524-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-150">, `from` yan tümcesinde sol bağıntıları genelleştirir ve bunları bir şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c5524-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="c5524-151">@No__t-0 yan tümcesindeki ifadeler, ek sözdizimi gerekmeden aynı yan tümcedeki önceki tanımlara (sol ve diğer tanımlar) başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="c5524-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-152">, ayrıca `group by` yan tümceleri içeren sorgularda ek kısıtlamalar uygular.</span><span class="sxs-lookup"><span data-stu-id="c5524-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="c5524-153">@No__t-0 yan tümcesindeki ve bu tür sorguların `having` yan tümcesindeki ifadeler yalnızca diğer adları aracılığıyla `group by` anahtarlarına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="c5524-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="c5524-154">Aşağıdaki yapı Transact-SQL ' te geçerlidir ancak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' da değildir:</span><span class="sxs-lookup"><span data-stu-id="c5524-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="c5524-155">Bunu yapmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="c5524-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="c5524-156">Tabloların (koleksiyonlar) sütunlarına (Özellikler) başvurma</span><span class="sxs-lookup"><span data-stu-id="c5524-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="c5524-157">@No__t-0 ' daki tüm sütun başvuruları tablo diğer adıyla nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c5524-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="c5524-158">Aşağıdaki yapı (`a` ' ın geçerli bir tablo olduğunu varsayarsak `T`) Transact-SQL içinde geçerli ancak [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' de değildir.</span><span class="sxs-lookup"><span data-stu-id="c5524-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="c5524-159">@No__t-0 formu</span><span class="sxs-lookup"><span data-stu-id="c5524-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="c5524-160">Tablo diğer adları `from` yan tümcesinde isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5524-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="c5524-161">Tablonun adı örtük diğer ad olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5524-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-162">aşağıdaki biçime de izin verir:</span><span class="sxs-lookup"><span data-stu-id="c5524-162">allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="c5524-163">Nesneler aracılığıyla gezinme</span><span class="sxs-lookup"><span data-stu-id="c5524-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="c5524-164">Transact-SQL, bir tablonun (bir satırı) sütunlarına başvurmak için "." gösterimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5524-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-165">, bir nesnenin özellikleri aracılığıyla gezinmeyi desteklemek için bu gösterimi (programlama dillerinden ödünç alınan) genişletir.</span><span class="sxs-lookup"><span data-stu-id="c5524-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="c5524-166">Örneğin, `p` kişi türünde bir ifadesiyse, bu kişinin adresinin şehrine başvurmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sözdizimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c5524-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="c5524-167">\* Desteği yok</span><span class="sxs-lookup"><span data-stu-id="c5524-167">No Support for \*</span></span>  
 <span data-ttu-id="c5524-168">Transact-SQL, tüm satır için bir diğer ad olarak nitelenmemiş \* söz dizimini ve nitelenmiş \* sözdizimi (t. \*) tablonun alanları için bir kısayol olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="c5524-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="c5524-169">Ayrıca Transact-SQL, null değerler içeren özel bir sayı (\*) toplaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5524-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-170">, \* yapısını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c5524-170">does not support the \* construct.</span></span> <span data-ttu-id="c5524-171">@No__t-0 ve `select T1.* from T1, T2...` biçimindeki Transact-SQL sorguları, sırasıyla `select value t from T as t` ve `select value t1 from T1 as t1, T2 as t2...` @no__t ile ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5524-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="c5524-172">Ayrıca, bu yapılar devralmayı (value substitutability), ancak `select *` çeşitlemeleri, belirtilen türün en üst düzey özellikleriyle sınırlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c5524-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-173">`count(*)` toplamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c5524-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="c5524-174">Bunun yerine `count(0)` kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5524-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="c5524-175">Gruplandırma ölçütü</span><span class="sxs-lookup"><span data-stu-id="c5524-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-176">`group by` anahtarların diğer adını destekler.</span><span class="sxs-lookup"><span data-stu-id="c5524-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="c5524-177">@No__t-0 yan tümcesindeki ve `having` yan tümcesindeki ifadeler, bu diğer adlar aracılığıyla `group by` anahtarlarına başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5524-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="c5524-178">Örneğin, bu @no__t 0 sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="c5524-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="c5524-179">... Aşağıdaki Transact-SQL ' e eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="c5524-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="c5524-180">Koleksiyon tabanlı toplamalar</span><span class="sxs-lookup"><span data-stu-id="c5524-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-181">iki tür toplamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="c5524-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="c5524-182">Koleksiyon tabanlı toplamalar koleksiyonlar üzerinde çalışır ve toplanmış sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="c5524-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="c5524-183">Bunlar sorgunun herhangi bir yerinde görünebilir ve `group by` yan tümcesi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c5524-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="c5524-184">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c5524-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-185">, SQL stili toplamlarını da destekler.</span><span class="sxs-lookup"><span data-stu-id="c5524-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="c5524-186">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c5524-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="c5524-187">ORDER BY yan tümcesi kullanımı</span><span class="sxs-lookup"><span data-stu-id="c5524-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="c5524-188">Transact-SQL `ORDER BY` yan tümcelerinin yalnızca en üstteki `SELECT .. FROM .. WHERE` bloğunda belirtilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5524-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="c5524-189">@No__t-0 ' da, iç içe bir `ORDER BY` ifadesi kullanabilirsiniz ve sorgu içinde herhangi bir yere yerleştirilebilir, ancak iç içe bir sorgudaki sıralama korunmaz.</span><span class="sxs-lookup"><span data-stu-id="c5524-189">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact AS C1
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="c5524-190">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="c5524-190">Identifiers</span></span>  
 <span data-ttu-id="c5524-191">Transact-SQL ' de tanımlayıcı karşılaştırması, geçerli veritabanının harmanlanmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="c5524-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="c5524-192">@No__t-0 ' da, tanımlayıcılar her zaman büyük/küçük harfe duyarlıdır ve aksan duyarlıdır (yani, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aksanlı ve aksanlı karakterler arasında ayrım yapar; örneğin, ' a ', ' ấ ' değerine eşit değildir).</span><span class="sxs-lookup"><span data-stu-id="c5524-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-193">, farklı kod sayfalarından farklı karakterler olarak görünen harflerin sürümlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c5524-193">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="c5524-194">Daha fazla bilgi için bkz. [giriş karakter kümesi](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c5524-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="c5524-195">Transact-SQL Işlevselliği Entity SQL kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="c5524-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="c5524-196">Aşağıdaki Transact-SQL işlevleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c5524-196">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="c5524-197">DML</span><span class="sxs-lookup"><span data-stu-id="c5524-197">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-198">şu anda DML deyimleri (INSERT, Update, Delete) için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c5524-198">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="c5524-199">DDL</span><span class="sxs-lookup"><span data-stu-id="c5524-199">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-200">geçerli sürümde DDL desteği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c5524-200">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="c5524-201">Kesin Programlama Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="c5524-201">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-202">, Transact-SQL ' den farklı olarak kesinlik temelli programlama için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c5524-202">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="c5524-203">Bunun yerine bir programlama dili kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5524-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="c5524-204">Gruplandırma Işlevleri</span><span class="sxs-lookup"><span data-stu-id="c5524-204">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-205">henüz gruplandırma işlevleri (örneğin, küp, toplama ve GROUPING_SET) için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c5524-205">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="c5524-206">Analitik Işlevler</span><span class="sxs-lookup"><span data-stu-id="c5524-206">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-207">, analitik işlevler için destek sağlamaz (henüz).</span><span class="sxs-lookup"><span data-stu-id="c5524-207">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="c5524-208">Yerleşik Işlevler, Işleçler</span><span class="sxs-lookup"><span data-stu-id="c5524-208">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-209">, Transact-SQL ' in yerleşik işlevlerinin ve işleçlerinin bir alt kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="c5524-209">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="c5524-210">Bu işleçler ve işlevler büyük olasılıkla ana mağaza sağlayıcıları tarafından desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5524-210">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-211">, bir sağlayıcı bildiriminde belirtilen mağazaya özgü işlevleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5524-211">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="c5524-212">Ayrıca Entity Framework, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ' ın kullanması için yerleşik ve Kullanıcı tanımlı depolama işlevlerini bildirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c5524-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="c5524-213">Yapılandıracak</span><span class="sxs-lookup"><span data-stu-id="c5524-213">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-214">sorgu ipuçları için mekanizmalar sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="c5524-214">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="c5524-215">Sorgu sonuçlarını toplu işleme</span><span class="sxs-lookup"><span data-stu-id="c5524-215">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c5524-216">sorgu sonuçlarını toplu olarak oluşturmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c5524-216">does not support batching query results.</span></span> <span data-ttu-id="c5524-217">Örneğin, aşağıda geçerli Transact-SQL (Batch olarak gönderme) verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c5524-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="c5524-218">Ancak eşdeğer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="c5524-218">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c5524-219">, komut başına yalnızca bir sonuç üreten sorgu bildirisini destekler.</span><span class="sxs-lookup"><span data-stu-id="c5524-219">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5524-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5524-220">See also</span></span>

- [<span data-ttu-id="c5524-221">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5524-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="c5524-222">Desteklenmeyen İfadeler</span><span class="sxs-lookup"><span data-stu-id="c5524-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
