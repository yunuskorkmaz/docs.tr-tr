---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 1a4bf8267ee5f036effc5f7bc91c28d1485b7612
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250857"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="2a099-102">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="2a099-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="2a099-103">Bu konu, ve Transact- [!INCLUDE[esql](../../../../../../includes/esql-md.md)] SQL arasındaki farkları açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a099-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="2a099-104">Devralma ve Ilişkiler desteği</span><span class="sxs-lookup"><span data-stu-id="2a099-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-105">doğrudan kavramsal varlık şemaları ile çalışarak devralma ve ilişkiler gibi kavramsal model özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="2a099-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="2a099-106">Devralmayla çalışırken, genellikle bir üst tür alt türünün örneklerini seçmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2a099-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="2a099-107">`oftype` İçindeki [](oftype-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] OfType işleci ( C# dizilerine benzer şekilde) bu yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a099-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="2a099-108">Koleksiyonlar için destek</span><span class="sxs-lookup"><span data-stu-id="2a099-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-109">koleksiyonları birinci sınıf varlıklar olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2a099-109">treats collections as first-class entities.</span></span> <span data-ttu-id="2a099-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a099-110">For example:</span></span>  
  
- <span data-ttu-id="2a099-111">Koleksiyon ifadeleri `from` yan tümcesinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2a099-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="2a099-112">`in`ve `exists` alt sorgular tüm koleksiyonlara izin verecek şekilde genelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2a099-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="2a099-113">Alt sorgu tek bir koleksiyon türüdür.</span><span class="sxs-lookup"><span data-stu-id="2a099-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="2a099-114">`e1 in e2`ve `exists(e)` bu işlemleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gerçekleştirmek için yapılardır.</span><span class="sxs-lookup"><span data-stu-id="2a099-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="2a099-115">,, Ve `union` `intersect` gibi`except`işlemleri, artık koleksiyonlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="2a099-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="2a099-116">Birleşimler koleksiyonlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="2a099-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="2a099-117">Ifadeler için destek</span><span class="sxs-lookup"><span data-stu-id="2a099-117">Support for Expressions</span></span>  
 <span data-ttu-id="2a099-118">Transact-SQL 'de alt sorgular (tablolar) ve ifadeler (satırlar ve sütunlar) vardır.</span><span class="sxs-lookup"><span data-stu-id="2a099-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="2a099-119">Koleksiyonları ve iç içe koleksiyonları [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemek için her şeyi bir ifadeye getirir.</span><span class="sxs-lookup"><span data-stu-id="2a099-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-120">, Transact-SQL ' den daha birleştirilebilir — her ifade her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a099-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="2a099-121">Sorgu ifadeleri her zaman öngörülen türlerin koleksiyonlarına neden olur ve koleksiyon ifadesine izin verildiğinde her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a099-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="2a099-122">' De [!INCLUDE[esql](../../../../../../includes/esql-md.md)]desteklenmeyen Transact-SQL ifadeleri hakkında daha fazla bilgi için bkz. [Desteklenmeyen ifadeler](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2a099-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="2a099-123">Tüm geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2a099-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="2a099-124">Alt sorguları Tekdüzen olarak Işleme</span><span class="sxs-lookup"><span data-stu-id="2a099-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="2a099-125">Tablo üzerinde vurgusu verildiğine göre Transact-SQL, alt sorgular için bağlama yorumu uygular.</span><span class="sxs-lookup"><span data-stu-id="2a099-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="2a099-126">Örneğin, `from` yan tümcesindeki bir alt sorgu bir çoklu küme (tablo) olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2a099-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="2a099-127">Ancak `select` yan tümcesinde kullanılan aynı alt sorgu skaler bir alt sorgu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="2a099-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="2a099-128">Benzer şekilde, bir `in` işlecin sol tarafında kullanılan bir alt sorgu skaler bir alt sorgu olarak değerlendirilir ve sağ taraftaki bir çoklu küme alt sorgusu olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="2a099-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-129">Bu farklılıkları ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2a099-129">eliminates these differences.</span></span> <span data-ttu-id="2a099-130">Bir ifade, kullanıldığı bağlama bağlı olmayan bir Tekdüzen yorumu içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2a099-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-131">tüm alt sorguları çoklu küme alt sorguları olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2a099-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="2a099-132">Alt sorgudan skaler bir değer isteniyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir koleksiyon üzerinde çalışan `anyelement` işleci (Bu durumda alt sorgu) sağlar ve koleksiyondan tek bir değer ayıklar.</span><span class="sxs-lookup"><span data-stu-id="2a099-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="2a099-133">Alt sorgular için örtük zorlamalar önleme</span><span class="sxs-lookup"><span data-stu-id="2a099-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="2a099-134">Tek biçimli alt sorgular için ilgili bir yan etkisi, alt sorguları skaler değerlere örtülü olarak dönüştürmedir.</span><span class="sxs-lookup"><span data-stu-id="2a099-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="2a099-135">Özellikle Transact-SQL ' de bir dizi çoklu küme (tek bir alan ile), veri türü alanın bulunduğu bir skalar değere örtülü olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="2a099-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-136">Bu örtük zorlaması desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2a099-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-137">bir koleksiyondan tek bir değer ayıklamak için AnyElement işlecini ve sorgu ifadesi sırasında satır sarmalayıcı `select value` oluşturulmasını önlemek için bir yan tümceyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a099-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="2a099-138">Değer seçin: Örtük satır sarmalayıcısı önleme</span><span class="sxs-lookup"><span data-stu-id="2a099-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="2a099-139">Bir Transact-SQL alt sorgusunda SELECT yan tümcesi, yan tümcesindeki öğelerin etrafında örtük olarak bir satır sarmalayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a099-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="2a099-140">Bu, yapı veya nesne koleksiyonları oluşturduğumuz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2a099-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="2a099-141">Transact-SQL, tek bir alanla RowType ve aynı veri türünde tek bir değer arasında örtük bir zorlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a099-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-142">örtük satır oluşturmayı atlamak için yantümcesağlar.`select value`</span><span class="sxs-lookup"><span data-stu-id="2a099-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="2a099-143">`select value` Yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="2a099-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="2a099-144">Böyle bir yan tümce kullanıldığında, `select` yan tümcesindeki öğeler etrafında satır sarmalayıcı oluşturulmadı ve istenen şeklin bir koleksiyonu üretilmeyebilir, örneğin:. `select value a`</span><span class="sxs-lookup"><span data-stu-id="2a099-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-145">Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a099-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="2a099-146">`select`projeksiyondaki bir veya daha fazla öğeyi alır ve alanları içeren bir veri kaydının aşağıdaki gibi sonuçlarını alır:</span><span class="sxs-lookup"><span data-stu-id="2a099-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="2a099-147">Sol bağıntı ve diğer ad</span><span class="sxs-lookup"><span data-stu-id="2a099-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="2a099-148">Transact-SQL içinde, belirli bir kapsamdaki ifadeler (veya `select` `from`gibi tek bir yan tümce), aynı kapsamda daha önce tanımlanan ifadelere başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="2a099-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="2a099-149">SQL 'in bazı diatıtılarını (Transact-SQL dahil), `from` yan tümcesinde bunların sınırlı biçimlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="2a099-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-150">`from` yan tümce içinde sol bağıntıları genelleştirir ve bunları bir şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2a099-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="2a099-151">`from` Yan tümcesindeki ifadeler, ek sözdizimi gerekmeden aynı yan tümce içindeki önceki tanımlara (sol ve diğer tanımlar) başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="2a099-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-152">Ayrıca, yan tümceleri içeren `group by` sorgularda ek kısıtlamalar uygular.</span><span class="sxs-lookup"><span data-stu-id="2a099-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="2a099-153">Bu tür sorguların `having` `group by` yan tümce ve yan tümcesindeki ifadeler yalnızca diğer adları aracılığıyla anahtarlara başvurabilir. `select`</span><span class="sxs-lookup"><span data-stu-id="2a099-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="2a099-154">Aşağıdaki yapı Transact-SQL ' te geçerlidir ancak içinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]yoktur:</span><span class="sxs-lookup"><span data-stu-id="2a099-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="2a099-155">Bunu yapmak [!INCLUDE[esql](../../../../../../includes/esql-md.md)]için:</span><span class="sxs-lookup"><span data-stu-id="2a099-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="2a099-156">Tabloların (koleksiyonlar) sütunlarına (Özellikler) başvurma</span><span class="sxs-lookup"><span data-stu-id="2a099-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="2a099-157">İçindeki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tüm sütun başvuruları tablo diğer adıyla nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="2a099-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="2a099-158">Aşağıdaki yapı (tablonun `a` `T`geçerli bir sütunu olduğunu varsayarak), Transact-SQL ' de geçerli, ancak içinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]değil.</span><span class="sxs-lookup"><span data-stu-id="2a099-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="2a099-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Form</span><span class="sxs-lookup"><span data-stu-id="2a099-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="2a099-160">Tablo diğer adları, `from` yan tümcesinde isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2a099-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="2a099-161">Tablonun adı örtük diğer ad olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a099-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-162">Aşağıdaki biçime de izin verir:</span><span class="sxs-lookup"><span data-stu-id="2a099-162">allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="2a099-163">Nesneler aracılığıyla gezinme</span><span class="sxs-lookup"><span data-stu-id="2a099-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="2a099-164">Transact-SQL, bir tablonun (bir satırı) sütunlarına başvurmak için "." gösterimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a099-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-165">bir nesnenin özellikleri aracılığıyla gezinmeyi desteklemek için bu gösterimi (programlama dillerinden ödünç alınan) genişletir.</span><span class="sxs-lookup"><span data-stu-id="2a099-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="2a099-166">Örneğin, `p` kişi türünde bir ifadesiyse, bu kişinin adresinin şehrine başvurmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sözdizimi aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="2a099-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="2a099-167">\* Desteği yok</span><span class="sxs-lookup"><span data-stu-id="2a099-167">No Support for \*</span></span>  
 <span data-ttu-id="2a099-168">Transact-SQL, tüm satır için bir diğer ad olarak nitelenmemiş \* sözdizimini ve bu tablonun alanları için \* bir kısayol olarak nitelenmiş\*sözdizimini (t.) destekler.</span><span class="sxs-lookup"><span data-stu-id="2a099-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="2a099-169">Ayrıca Transact-SQL, null değerler içeren özel bir Count (\*) toplamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2a099-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-170">\* yapısını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2a099-170">does not support the \* construct.</span></span> <span data-ttu-id="2a099-171">Formunun `select * from T` Transact-SQL sorguları ve `select T1.* from T1, T2...` sırasıyla ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...`olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="2a099-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="2a099-172">Ayrıca, bu yapılar devralma (değer substitutability), ancak `select *` varyantlar, belirtilen türün en üst düzey özellikleriyle sınırlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2a099-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-173">`count(*)` toplamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2a099-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="2a099-174">Bunun yerine `count(0)` kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a099-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="2a099-175">Gruplandırma ölçütü</span><span class="sxs-lookup"><span data-stu-id="2a099-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-176">anahtarların diğer adını `group by` destekler.</span><span class="sxs-lookup"><span data-stu-id="2a099-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="2a099-177">Yan tümce ve `having` yan tümcesindeki ifadeler, `group by` bu diğer adlar aracılığıyla anahtarlara başvurmalıdır. `select`</span><span class="sxs-lookup"><span data-stu-id="2a099-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="2a099-178">Örneğin, bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="2a099-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="2a099-179">... Aşağıdaki Transact-SQL ' e eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="2a099-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="2a099-180">Koleksiyon tabanlı toplamalar</span><span class="sxs-lookup"><span data-stu-id="2a099-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-181">iki tür toplamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="2a099-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="2a099-182">Koleksiyon tabanlı toplamalar koleksiyonlar üzerinde çalışır ve toplanmış sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="2a099-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="2a099-183">Bunlar sorgunun herhangi bir yerinde görünebilir ve `group by` yan tümce gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="2a099-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="2a099-184">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a099-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-185">, SQL stili toplamlarını da destekler.</span><span class="sxs-lookup"><span data-stu-id="2a099-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="2a099-186">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a099-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="2a099-187">ORDER BY yan tümcesi kullanımı</span><span class="sxs-lookup"><span data-stu-id="2a099-187">ORDER BY Clause Usage</span></span>  
 <span data-ttu-id="2a099-188">Transact-SQL ORDER BY yan tümcelerinin yalnızca en üstteki SELECT içinde belirtilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a099-188">Transact-SQL allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="2a099-189">KAYNAK..</span><span class="sxs-lookup"><span data-stu-id="2a099-189">FROM ..</span></span> <span data-ttu-id="2a099-190">WHERE bloğu.</span><span class="sxs-lookup"><span data-stu-id="2a099-190">WHERE block.</span></span> <span data-ttu-id="2a099-191">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , iç içe geçmiş bir ifade kullanabilirsiniz ve sorgu içinde herhangi bir yere yerleştirilebilir, ancak iç içe bir sorgudaki sıralama korunmaz.</span><span class="sxs-lookup"><span data-stu-id="2a099-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name  
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
  
## <a name="identifiers"></a><span data-ttu-id="2a099-192">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="2a099-192">Identifiers</span></span>  
 <span data-ttu-id="2a099-193">Transact-SQL ' de tanımlayıcı karşılaştırması, geçerli veritabanının harmanlanmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="2a099-193">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="2a099-194">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)]tanımlayıcılar her zaman büyük/küçük harfe duyarlıdır ve aksan duyarlıdır (yani [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , aksanlı ve aksanlı karakterler arasında ayrım yapar; örneğin, ' a ', ' ấ ' değerine eşit değildir).</span><span class="sxs-lookup"><span data-stu-id="2a099-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-195">aynı görünen, ancak farklı kod sayfalarından farklı karakter olan harflerin sürümlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2a099-195">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="2a099-196">Daha fazla bilgi için bkz. [giriş karakter kümesi](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2a099-196">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="2a099-197">Transact-SQL Işlevselliği Entity SQL kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="2a099-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="2a099-198">Aşağıdaki Transact-SQL işlevselliği ' de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2a099-198">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="2a099-199">DML</span><span class="sxs-lookup"><span data-stu-id="2a099-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-200">Şu anda DML deyimleri (INSERT, Update, Delete) için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2a099-200">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="2a099-201">DDL</span><span class="sxs-lookup"><span data-stu-id="2a099-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-202">geçerli sürümde DDL desteği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2a099-202">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="2a099-203">Kesin Programlama Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="2a099-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-204">, Transact-SQL ' den farklı olarak, kesinlik temelli programlama için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2a099-204">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="2a099-205">Bunun yerine bir programlama dili kullanın.</span><span class="sxs-lookup"><span data-stu-id="2a099-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="2a099-206">Gruplandırma Işlevleri</span><span class="sxs-lookup"><span data-stu-id="2a099-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-207">henüz gruplandırma işlevleri için destek sağlamaz (örneğin, CUBE, ROLLUP ve GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="2a099-207">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="2a099-208">Analitik Işlevler</span><span class="sxs-lookup"><span data-stu-id="2a099-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-209">(henüz) analitik işlevler için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2a099-209">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="2a099-210">Yerleşik Işlevler, Işleçler</span><span class="sxs-lookup"><span data-stu-id="2a099-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-211">Transact-SQL ' in yerleşik işlevlerinin ve işleçlerinin bir alt kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="2a099-211">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="2a099-212">Bu işleçler ve işlevler büyük olasılıkla ana mağaza sağlayıcıları tarafından desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2a099-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-213">bir sağlayıcı bildiriminde belirtilen mağazaya özgü işlevleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a099-213">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="2a099-214">Ayrıca, kullanımı için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] yerleşik ve Kullanıcı tanımlı var olan depolama işlevlerini bildirmenize olanaktanır.[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a099-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="2a099-215">Yapılandıracak</span><span class="sxs-lookup"><span data-stu-id="2a099-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-216">sorgu ipuçları için mekanizmalar sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2a099-216">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="2a099-217">Sorgu sonuçlarını toplu işleme</span><span class="sxs-lookup"><span data-stu-id="2a099-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-218">sorgu sonuçlarını toplu olarak oluşturmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2a099-218">does not support batching query results.</span></span> <span data-ttu-id="2a099-219">Örneğin, aşağıda geçerli Transact-SQL (Batch olarak gönderme) verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2a099-219">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="2a099-220">Ancak eşdeğer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir değer desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="2a099-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2a099-221">komut başına yalnızca bir sonuç oluşturan sorgu bildirisini destekler.</span><span class="sxs-lookup"><span data-stu-id="2a099-221">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a099-222">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a099-222">See also</span></span>

- [<span data-ttu-id="2a099-223">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2a099-223">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="2a099-224">Desteklenmeyen İfadeler</span><span class="sxs-lookup"><span data-stu-id="2a099-224">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
