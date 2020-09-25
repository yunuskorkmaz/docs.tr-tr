---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 9433e7a7ffdc3a7e32900981dca95eefde32f290
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204443"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="f5a2d-102">Entity SQL Transact-SQL ' den farklı</span><span class="sxs-lookup"><span data-stu-id="f5a2d-102">How Entity SQL differs from Transact-SQL</span></span>

<span data-ttu-id="f5a2d-103">Bu makalede Entity SQL ve Transact-SQL arasındaki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-103">This article describes the differences between Entity SQL and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="f5a2d-104">Devralma ve Ilişkiler desteği</span><span class="sxs-lookup"><span data-stu-id="f5a2d-104">Inheritance and Relationships Support</span></span>  

 <span data-ttu-id="f5a2d-105">Entity SQL doğrudan kavramsal varlık şemalarıyla çalışarak, devralma ve ilişkiler gibi kavramsal model özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-105">Entity SQL works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="f5a2d-106">Devralmayla çalışırken, genellikle bir üst tür alt türünün örneklerini seçmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="f5a2d-107">Entity SQL [oftype](oftype-entity-sql.md) ( `oftype` C# dizilerinde olduğu gibi) OfType işleci bu yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-107">The [oftype](oftype-entity-sql.md) operator in Entity SQL (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="f5a2d-108">Koleksiyonlar için destek</span><span class="sxs-lookup"><span data-stu-id="f5a2d-108">Support for Collections</span></span>  

 <span data-ttu-id="f5a2d-109">Entity SQL, koleksiyonları birinci sınıf varlıklar olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-109">Entity SQL treats collections as first-class entities.</span></span> <span data-ttu-id="f5a2d-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-110">For example:</span></span>  
  
- <span data-ttu-id="f5a2d-111">Koleksiyon ifadeleri `from` yan tümcesinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="f5a2d-112">`in` ve alt `exists` sorgular tüm koleksiyonlara izin verecek şekilde genelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="f5a2d-113">Alt sorgu tek bir koleksiyon türüdür.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="f5a2d-114">`e1 in e2` ve `exists(e)` Bu işlemleri gerçekleştirmek için Entity SQL yapılarıdır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-114">`e1 in e2` and `exists(e)` are the Entity SQL constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="f5a2d-115">,, Ve gibi işlemleri `union` , `intersect` `except` artık koleksiyonlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="f5a2d-116">Birleşimler koleksiyonlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="f5a2d-117">Ifadeler için destek</span><span class="sxs-lookup"><span data-stu-id="f5a2d-117">Support for Expressions</span></span>  

 <span data-ttu-id="f5a2d-118">Transact-SQL 'de alt sorgular (tablolar) ve ifadeler (satırlar ve sütunlar) vardır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="f5a2d-119">Koleksiyonları ve iç içe koleksiyonları desteklemek için Entity SQL her şeyi bir ifadeye getirir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-119">To support collections and nested collections, Entity SQL makes everything an expression.</span></span> <span data-ttu-id="f5a2d-120">Entity SQL Transact-SQL ' den daha birleştirilebilir — her ifade her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-120">Entity SQL is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="f5a2d-121">Sorgu ifadeleri her zaman öngörülen türlerin koleksiyonlarına neden olur ve koleksiyon ifadesine izin verildiğinde her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="f5a2d-122">Entity SQL desteklenmeyen Transact-SQL ifadeleri hakkında daha fazla bilgi için bkz. [Desteklenmeyen ifadeler](unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f5a2d-122">For information about Transact-SQL expressions that are not supported in Entity SQL, see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="f5a2d-123">Tüm geçerli Entity SQL sorguları aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-123">The following are all valid Entity SQL queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="f5a2d-124">Alt sorguları Tekdüzen olarak Işleme</span><span class="sxs-lookup"><span data-stu-id="f5a2d-124">Uniform Treatment of Subqueries</span></span>  

 <span data-ttu-id="f5a2d-125">Tablo üzerinde vurgusu verildiğine göre Transact-SQL, alt sorgular için bağlama yorumu uygular.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="f5a2d-126">Örneğin, yan tümcesindeki bir alt sorgu `from` bir çoklu küme (tablo) olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="f5a2d-127">Ancak yan tümcesinde kullanılan aynı alt sorgu `select` skaler bir alt sorgu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="f5a2d-128">Benzer şekilde, bir işlecin sol tarafında kullanılan bir alt sorgu `in` skaler bir alt sorgu olarak değerlendirilir ve sağ taraftaki bir çoklu küme alt sorgusu olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 <span data-ttu-id="f5a2d-129">Entity SQL bu farklılıkları ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-129">Entity SQL eliminates these differences.</span></span> <span data-ttu-id="f5a2d-130">Bir ifade, kullanıldığı bağlama bağlı olmayan bir Tekdüzen yorumu içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> <span data-ttu-id="f5a2d-131">Entity SQL tüm alt sorguları çoklu küme alt sorguları olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-131">Entity SQL considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="f5a2d-132">Alt sorgudan skaler bir değer isteniyorsa Entity SQL, `anyelement` bir koleksiyon üzerinde çalışan işleci (Bu durumda alt sorgu) sağlar ve koleksiyondan tek bir değer ayıklar.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-132">If a scalar value is desired from the subquery, Entity SQL provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="f5a2d-133">Alt sorgular için örtük zorlamalar önleme</span><span class="sxs-lookup"><span data-stu-id="f5a2d-133">Avoiding Implicit Coercions for Subqueries</span></span>  

 <span data-ttu-id="f5a2d-134">Tek biçimli alt sorgular için ilgili bir yan etkisi, alt sorguları skaler değerlere örtülü olarak dönüştürmedir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="f5a2d-135">Özellikle Transact-SQL ' de bir dizi çoklu küme (tek bir alan ile), veri türü alanın bulunduğu bir skalar değere örtülü olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 <span data-ttu-id="f5a2d-136">Entity SQL, bu örtülü zorlaması desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-136">Entity SQL does not support this implicit coercion.</span></span> <span data-ttu-id="f5a2d-137">Entity SQL `ANYELEMENT` , bir koleksiyondan tek bir değer ayıklamaya ve `select value` sorgu ifadesi sırasında satır sarmalayıcı oluşturmaktan kaçınmak için bir yan tümce sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-137">Entity SQL provides the `ANYELEMENT` operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="f5a2d-138">Değer seçin: örtük satır sarmalayıcısı ' ı önleme</span><span class="sxs-lookup"><span data-stu-id="f5a2d-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  

 <span data-ttu-id="f5a2d-139">Bir Transact-SQL alt sorgusunda SELECT yan tümcesi, yan tümcesindeki öğelerin etrafında örtük olarak bir satır sarmalayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="f5a2d-140">Bu, yapı veya nesne koleksiyonları oluşturduğumuz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="f5a2d-141">Transact-SQL `rowtype` , bir alan ile aynı veri türünde tek bir değer arasında örtük bir zorlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-141">Transact-SQL allows an implicit coercion between a `rowtype` with one field and a singleton value of the same data type.</span></span>  
  
 <span data-ttu-id="f5a2d-142">Entity SQL `select value` örtük satır oluşturmayı atlamak için yan tümce sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-142">Entity SQL provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="f5a2d-143">Yan tümcesinde yalnızca bir öğe belirtilebilir `select value` .</span><span class="sxs-lookup"><span data-stu-id="f5a2d-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="f5a2d-144">Böyle bir yan tümce kullanıldığında, yan tümcesindeki öğelerin çevresine hiçbir satır sarmalayıcı oluşturulmadı `select` ve örneğin, istenen şeklin bir koleksiyonu oluşturulabilir `select value a` .</span><span class="sxs-lookup"><span data-stu-id="f5a2d-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example, `select value a`.</span></span>  
  
 <span data-ttu-id="f5a2d-145">Entity SQL Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-145">Entity SQL also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="f5a2d-146">`select` projeksiyde bir veya daha fazla öğe alır ve alanlarla veri kaydına neden olur:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-146">`select` takes one or more elements in the projection and results in a data record with fields:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="f5a2d-147">Sol bağıntı ve diğer ad</span><span class="sxs-lookup"><span data-stu-id="f5a2d-147">Left Correlation and Aliasing</span></span>  

 <span data-ttu-id="f5a2d-148">Transact-SQL içinde, belirli bir kapsamdaki ifadeler (veya gibi tek bir yan `select` tümce `from` ), aynı kapsamda daha önce tanımlanan ifadelere başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="f5a2d-149">SQL 'in bazı diatıtılarını (Transact-SQL dahil), yan tümcesinde bunların sınırlı biçimlerini destekler `from` .</span><span class="sxs-lookup"><span data-stu-id="f5a2d-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 <span data-ttu-id="f5a2d-150">Entity SQL yan tümcelerinde sol bağıntıları genelleştirir `from` ve bunları bir şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-150">Entity SQL generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="f5a2d-151">`from`Yan tümcesindeki ifadeler, ek sözdizimi gerekmeden aynı yan tümce içindeki önceki tanımlara (sol ve diğer tanımlar) başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 <span data-ttu-id="f5a2d-152">Entity SQL Ayrıca, yan tümceleri içeren sorgularda ek kısıtlamalar uygular `group by` .</span><span class="sxs-lookup"><span data-stu-id="f5a2d-152">Entity SQL also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="f5a2d-153">`select` `having` Bu tür sorguların yan tümce ve yan tümcesindeki ifadeler yalnızca `group by` diğer adları aracılığıyla anahtarlara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="f5a2d-154">Aşağıdaki yapı Transact-SQL ' te geçerlidir ancak Entity SQL değildir:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-154">The following construct is valid in Transact-SQL but are not in Entity SQL:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="f5a2d-155">Bunu yapmak için Entity SQL:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-155">To do this in Entity SQL:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="f5a2d-156">Tabloların (koleksiyonlar) sütunlarına (Özellikler) başvurma</span><span class="sxs-lookup"><span data-stu-id="f5a2d-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  

 <span data-ttu-id="f5a2d-157">Entity SQL tüm sütun başvuruları tablo diğer adıyla nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-157">All column references in Entity SQL must be qualified with the table alias.</span></span> <span data-ttu-id="f5a2d-158">Aşağıdaki yapı ( `a` tablonun geçerli bir sütunu olduğunu varsayarak `T` ) Transact-SQL ' de geçerlidir ancak Entity SQL değildir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in Entity SQL.</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="f5a2d-159">Entity SQL form</span><span class="sxs-lookup"><span data-stu-id="f5a2d-159">The Entity SQL form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="f5a2d-160">Tablo diğer adları, `from` yan tümcesinde isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="f5a2d-161">Tablonun adı örtük diğer ad olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-161">The name of the table is used as the implicit alias.</span></span> <span data-ttu-id="f5a2d-162">Entity SQL aşağıdaki biçime de izin verir:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-162">Entity SQL allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="f5a2d-163">Nesneler aracılığıyla gezinme</span><span class="sxs-lookup"><span data-stu-id="f5a2d-163">Navigation Through Objects</span></span>  

 <span data-ttu-id="f5a2d-164">Transact-SQL, bir tablonun (bir satırı) sütunlarına başvurmak için "." gösterimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> <span data-ttu-id="f5a2d-165">Entity SQL, bir nesnenin özellikleri aracılığıyla gezinmeyi desteklemek için bu gösterimi (programlama dillerinden ödünç alınan) genişletir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-165">Entity SQL extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="f5a2d-166">Örneğin, `p` kişi türünde bir ifadesiyse, bu kişinin adresinin şehrine başvurmak için Entity SQL sözdizimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-166">For example, if `p` is an expression of type Person, the following is the Entity SQL syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="f5a2d-167">İçin destek yok \*</span><span class="sxs-lookup"><span data-stu-id="f5a2d-167">No Support for \*</span></span>  

 <span data-ttu-id="f5a2d-168">Transact-SQL, \* tüm satır için bir diğer ad olarak nitelenmemiş sözdizimini ve \* \* Bu tablonun alanları için bir kısayol olarak nitelenmiş sözdizimini (t.) destekler.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="f5a2d-169">Ayrıca Transact-SQL, null değerler içeren özel bir Count ( \* ) toplamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 <span data-ttu-id="f5a2d-170">Entity SQL, \* yapısını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-170">Entity SQL does not support the \* construct.</span></span> <span data-ttu-id="f5a2d-171">Formunun Transact-SQL sorguları `select * from T` ve `select T1.* from T1, T2...` sırasıyla Entity SQL olarak ifade edilebilir `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...` .</span><span class="sxs-lookup"><span data-stu-id="f5a2d-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in Entity SQL as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="f5a2d-172">Ayrıca, bu yapılar devralma (değer substitutability), ancak `select *` varyantlar, belirtilen türün en üst düzey özellikleriyle sınırlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 <span data-ttu-id="f5a2d-173">Entity SQL, `count(*)` toplamı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-173">Entity SQL does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="f5a2d-174">Bunun yerine `count(0)` kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="f5a2d-175">Gruplandırma ölçütü</span><span class="sxs-lookup"><span data-stu-id="f5a2d-175">Changes to Group By</span></span>  

 <span data-ttu-id="f5a2d-176">Entity SQL anahtarların diğer adını destekler `group by` .</span><span class="sxs-lookup"><span data-stu-id="f5a2d-176">Entity SQL supports aliasing of `group by` keys.</span></span> <span data-ttu-id="f5a2d-177">`select`Yan tümce ve `having` yan tümcesindeki ifadeler, `group by` Bu diğer adlar aracılığıyla anahtarlara başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="f5a2d-178">Örneğin, bu Entity SQL söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-178">For example, this Entity SQL syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="f5a2d-179">... Aşağıdaki Transact-SQL ' e eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="f5a2d-180">Koleksiyon tabanlı toplamalar</span><span class="sxs-lookup"><span data-stu-id="f5a2d-180">Collection-Based Aggregates</span></span>  

 <span data-ttu-id="f5a2d-181">Entity SQL iki tür toplamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-181">Entity SQL supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="f5a2d-182">Koleksiyon tabanlı toplamalar koleksiyonlar üzerinde çalışır ve toplanmış sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="f5a2d-183">Bunlar sorgunun herhangi bir yerinde görünebilir ve `group by` yan tümce gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="f5a2d-184">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 <span data-ttu-id="f5a2d-185">Entity SQL Ayrıca SQL stili toplamlarını da destekler.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-185">Entity SQL also supports SQL-style aggregates.</span></span> <span data-ttu-id="f5a2d-186">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="f5a2d-187">ORDER BY yan tümcesi kullanımı</span><span class="sxs-lookup"><span data-stu-id="f5a2d-187">ORDER BY Clause Usage</span></span>  

<span data-ttu-id="f5a2d-188">Transact-SQL `ORDER BY` yan tümcelerinin yalnızca en üstteki blokta belirtilmesini sağlar `SELECT .. FROM .. WHERE` .</span><span class="sxs-lookup"><span data-stu-id="f5a2d-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="f5a2d-189">Entity SQL, iç içe geçmiş bir ifade kullanabilirsiniz `ORDER BY` ve sorgu içinde herhangi bir yere yerleştirilebilir, ancak iç içe bir sorgudaki sıralama korunmaz.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-189">In Entity SQL, you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="f5a2d-190">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="f5a2d-190">Identifiers</span></span>  

 <span data-ttu-id="f5a2d-191">Transact-SQL ' de tanımlayıcı karşılaştırması, geçerli veritabanının harmanlanmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="f5a2d-192">Entity SQL, tanımlayıcılar her zaman büyük/küçük harfe duyarlıdır ve aksan duyarlıdır (yani, Entity SQL aksanlı ve aksanlı karakterler arasında ayrım yapar; örneğin, ' a ', ' ấ ' değerine eşit değildir).</span><span class="sxs-lookup"><span data-stu-id="f5a2d-192">In Entity SQL, identifiers are always case insensitive and accent sensitive (that is, Entity SQL distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> <span data-ttu-id="f5a2d-193">Entity SQL, aynı olan ancak farklı kod sayfalarından farklı karakter olan harflerin sürümlerini ele alır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-193">Entity SQL treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="f5a2d-194">Daha fazla bilgi için bkz. [giriş karakter kümesi](input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f5a2d-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="f5a2d-195">Transact-SQL Işlevselliği Entity SQL kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="f5a2d-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  

 <span data-ttu-id="f5a2d-196">Aşağıdaki Transact-SQL işlevleri Entity SQL ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-196">The following Transact-SQL functionality is not available in Entity SQL.</span></span>  
  
 <span data-ttu-id="f5a2d-197">DML</span><span class="sxs-lookup"><span data-stu-id="f5a2d-197">DML</span></span>  
 <span data-ttu-id="f5a2d-198">Entity SQL Şu anda DML deyimleri (INSERT, Update, Delete) için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-198">Entity SQL currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="f5a2d-199">DDL</span><span class="sxs-lookup"><span data-stu-id="f5a2d-199">DDL</span></span>  
 <span data-ttu-id="f5a2d-200">Entity SQL geçerli sürümde DDL desteği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-200">Entity SQL provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="f5a2d-201">Kesin Programlama Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="f5a2d-201">Imperative Programming</span></span>  
 <span data-ttu-id="f5a2d-202">Entity SQL, Transact-SQL ' den farklı olarak, kesinlik temelli programlama için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-202">Entity SQL provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="f5a2d-203">Bunun yerine bir programlama dili kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="f5a2d-204">Gruplandırma Işlevleri</span><span class="sxs-lookup"><span data-stu-id="f5a2d-204">Grouping Functions</span></span>  
 <span data-ttu-id="f5a2d-205">Entity SQL, gruplandırma işlevlerini (örneğin, küp, toplama ve GROUPING_SET) için henüz destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-205">Entity SQL does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="f5a2d-206">Analitik İşlevler</span><span class="sxs-lookup"><span data-stu-id="f5a2d-206">Analytic Functions</span></span>  
 <span data-ttu-id="f5a2d-207">Entity SQL, analitik işlevler için destek sağlamaz (henüz).</span><span class="sxs-lookup"><span data-stu-id="f5a2d-207">Entity SQL does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="f5a2d-208">Yerleşik Işlevler, Işleçler</span><span class="sxs-lookup"><span data-stu-id="f5a2d-208">Built-in Functions, Operators</span></span>  
 <span data-ttu-id="f5a2d-209">Entity SQL, Transact-SQL ' in yerleşik işlevlerinin ve işleçlerinin bir alt kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-209">Entity SQL supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="f5a2d-210">Bu işleçler ve işlevler büyük olasılıkla ana mağaza sağlayıcıları tarafından desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-210">These operators and functions are likely to be supported by the major store providers.</span></span> <span data-ttu-id="f5a2d-211">Entity SQL, bir sağlayıcı bildiriminde belirtilen mağazaya özgü işlevleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-211">Entity SQL uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="f5a2d-212">Ayrıca Entity Framework, Entity SQL kullanılmak üzere yerleşik ve Kullanıcı tanımlı mevcut depolama işlevlerini bildirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for Entity SQL to use.</span></span>  
  
 <span data-ttu-id="f5a2d-213">Yapılandıracak</span><span class="sxs-lookup"><span data-stu-id="f5a2d-213">Hints</span></span>  
 <span data-ttu-id="f5a2d-214">Entity SQL sorgu ipuçları için mekanizmalar sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-214">Entity SQL does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="f5a2d-215">Sorgu sonuçlarını toplu işleme</span><span class="sxs-lookup"><span data-stu-id="f5a2d-215">Batching Query Results</span></span>  
 <span data-ttu-id="f5a2d-216">Entity SQL sorgu sonuçlarını toplu olarak oluşturmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-216">Entity SQL does not support batching query results.</span></span> <span data-ttu-id="f5a2d-217">Örneğin, aşağıda geçerli Transact-SQL (Batch olarak gönderme) verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="f5a2d-218">Ancak eşdeğer Entity SQL desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="f5a2d-218">However, the equivalent Entity SQL is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 <span data-ttu-id="f5a2d-219">Entity SQL, komut başına yalnızca bir sonucu üreten sorgu bildirisini destekler.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-219">Entity SQL only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a2d-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5a2d-220">See also</span></span>

- [<span data-ttu-id="f5a2d-221">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f5a2d-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="f5a2d-222">Desteklenmeyen İfadeler</span><span class="sxs-lookup"><span data-stu-id="f5a2d-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
