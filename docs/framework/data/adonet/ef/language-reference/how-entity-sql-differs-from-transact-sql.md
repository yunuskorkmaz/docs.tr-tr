---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 299cb9bbe90c72619cf809a8fc673fca456bd6fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150237"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="d4ab5-102">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="d4ab5-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="d4ab5-103">Bu konu, Transact-SQL arasındaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] farkları açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and Transact-SQL.</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="d4ab5-104">Kalıtım ve İlişkiler Desteği</span><span class="sxs-lookup"><span data-stu-id="d4ab5-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-105">doğrudan kavramsal varlık şemaları ile çalışır ve kalıtım ve ilişkiler gibi kavramsal model özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="d4ab5-106">Devralma yla çalışırken, genellikle bir alt tür örneklerini bir üst tür örnekleri koleksiyonundan seçmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="d4ab5-107">(C# Sequences'dekine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] `oftype` benzer) [oftipi](oftype-entity-sql.md) işleci bu özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-107">The [oftype](oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="d4ab5-108">Koleksiyonlar için Destek</span><span class="sxs-lookup"><span data-stu-id="d4ab5-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-109">koleksiyonları birinci sınıf varlıklar olarak ele alır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-109">treats collections as first-class entities.</span></span> <span data-ttu-id="d4ab5-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-110">For example:</span></span>  
  
- <span data-ttu-id="d4ab5-111">Koleksiyon ifadeleri bir `from` yan tümcede geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="d4ab5-112">`in`ve `exists` alt sorgular herhangi bir koleksiyona izin verecek şekilde genelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="d4ab5-113">Alt sorgu, bir tür koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="d4ab5-114">`e1 in e2`ve `exists(e)` bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlemleri gerçekleştirmek için yapılardır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="d4ab5-115">" ve `union` `intersect` `except`, şimdi koleksiyonlar üzerinde çalışır gibi işlemleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="d4ab5-116">Birleştirmeler koleksiyonlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="d4ab5-117">İfadeler için Destek</span><span class="sxs-lookup"><span data-stu-id="d4ab5-117">Support for Expressions</span></span>  
 <span data-ttu-id="d4ab5-118">Transact-SQL alt sorguları (tablolar) ve ifadeler (satırlar ve sütunlar) vardır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-118">Transact-SQL has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="d4ab5-119">Koleksiyonları ve iç içe koleksiyonları [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklemek için, her şeyi bir ifade yapar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-120">Transact-SQL'den daha fazla kullanılabilir— her ifade her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-120">is more composable than Transact-SQL—every expression can be used anywhere.</span></span> <span data-ttu-id="d4ab5-121">Sorgu ifadeleri her zaman yansıtılan türlerin koleksiyonlarıyla sonuçlanır ve koleksiyon ifadesine izin verilen her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="d4ab5-122">Desteklenmeyen [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Transact-SQL ifadeleri hakkında bilgi [için](unsupported-expressions-entity-sql.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-122">For information about Transact-SQL expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="d4ab5-123">Geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguların tümü şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```sql  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="d4ab5-124">Alt Sorguların Tek Tip Tedavisi</span><span class="sxs-lookup"><span data-stu-id="d4ab5-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="d4ab5-125">Transact-SQL, tablolara verdiği önem göz önüne alındığında alt sorguların bağlamsal yorumunu gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-125">Given its emphasis on tables, Transact-SQL performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="d4ab5-126">Örneğin, `from` yan tümcedeki bir alt sorgu çok ayarlı (tablo) olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="d4ab5-127">Ancak `select` yan tümcede kullanılan aynı alt sorgu skaler alt sorgu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="d4ab5-128">Benzer şekilde, bir `in` işleç sol tarafında kullanılan bir alt sorgu skaler alt sorgu olarak kabul edilirken, sağ tarafında çok ayarlı bir alt sorgu olması bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-129">bu farklılıkları ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-129">eliminates these differences.</span></span> <span data-ttu-id="d4ab5-130">Bir ifadenin kullanıldığı içeriğe bağlı olmayan tek bir yorumu vardır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-131">tüm alt sorguları çok ayarlı alt sorgular olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="d4ab5-132">Alt sorgudan skaler bir değer isteniyorsa, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir koleksiyon üzerinde çalışan `anyelement` işleci sağlar (bu durumda, alt sorgu) ve koleksiyondan singleton değerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="d4ab5-133">Alt Sorgular için Örtük Zorlamalardan Kaçınma</span><span class="sxs-lookup"><span data-stu-id="d4ab5-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="d4ab5-134">Alt sorguların tek tip tedavisinin ilgili yan etkisi, alt sorguların skaler değerlere örtülü olarak dönüştürülmesidir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="d4ab5-135">Özellikle, Transact-SQL'de, (tek bir alana sahip) bir satır kümesi dolaylı olarak, veri türü alanın değeri olan skaler bir değere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-135">Specifically, in Transact-SQL, a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-136">bu örtük zorlamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-137">ANYELEMENT işlecinin bir koleksiyondan singleton değerini `select value` ayıklamasını ve sorgu ifadesi sırasında satır sarıcı oluşturmamasını önlemek için bir yan tümce sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="d4ab5-138">Değer Seçin: Örtük Satır Sarıcı'dan Kaçınma</span><span class="sxs-lookup"><span data-stu-id="d4ab5-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="d4ab5-139">Transact-SQL alt sorgusundaki select yan tümcesi, yan tümcedeki öğelerin etrafında dolaylı olarak bir satır sarıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-139">The select clause in a Transact-SQL subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="d4ab5-140">Bu, skaler veya nesnelerin koleksiyonlarını oluşturamayacağımız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-140">This implies that we cannot create collections of scalars or objects.</span></span> <span data-ttu-id="d4ab5-141">Transact-SQL, bir alana sahip bir satır türü ile aynı veri türünün singleton değeri arasında örtük bir zorlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-141">Transact-SQL allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-142">örtük `select value` satır konstrüksiyonu atlamak için yan tümce sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="d4ab5-143">Bir yan tümcede `select value` yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="d4ab5-144">Böyle bir yan tümce kullanıldığında, `select` yan tümcedeki öğelerin etrafına satır sarıcı oluşturulmaz ve örneğin `select value a`istenen şeklin bir koleksiyonu oluşturulabilir: .</span><span class="sxs-lookup"><span data-stu-id="d4ab5-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-145">ayrıca satır oluşturucuya rasgele satırlar oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="d4ab5-146">`select`projeksiyonda bir veya daha fazla öğe alır ve aşağıdaki gibi alanları içeren bir veri kaydı yla sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="d4ab5-147">Sol Korelasyon ve Diğer Adlama</span><span class="sxs-lookup"><span data-stu-id="d4ab5-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="d4ab5-148">Transact-SQL'de, belirli bir kapsamdaki ifadeler `select` (örneğin veya `from`) aynı kapsamda daha önce tanımlanan ifadelere başvuruyapamaz.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-148">In Transact-SQL, expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="d4ab5-149">SQL'in bazı lehçeleri (Transact-SQL dahil) `from` yan tümcedeki sınırlı formları destekler.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-149">Some dialects of SQL (including Transact-SQL) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-150">`from` maddedeki sol bağıntıları genelleştirir ve bunları eşit davranır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="d4ab5-151">Yan tümcedeki `from` ifadeler, ek sözdizimine gerek kalmadan aynı yan tümcedeki önceki tanımlara (soldaki tanımlar) başvuru yapabilir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-152">yan tümceleri içeren `group by` sorgulara ek kısıtlamalar da uygular.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="d4ab5-153">Bu tür `select` sorguların `having` yan tümcesindeki ve `group by` yan tümcesindeki ifadeler yalnızca diğer adlar aracılığıyla anahtarlara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="d4ab5-154">Aşağıdaki yapı Transact-SQL'de geçerlidir [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ancak aşağıdaki nde değildir:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-154">The following construct is valid in Transact-SQL but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELECT t.x + t.y FROM T AS t group BY t.x + t.y
```  
  
 <span data-ttu-id="d4ab5-155">Bunu yapmak [!INCLUDE[esql](../../../../../../includes/esql-md.md)]için:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```sql  
SELET k FROM T AS t GROUP BY (t.x + t.y) AS k
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="d4ab5-156">Tabloların (Koleksiyonların Özellikleri) Başvuru Sütunları (Özellikleri)</span><span class="sxs-lookup"><span data-stu-id="d4ab5-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="d4ab5-157">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sütun başvuruları tablo diğer adı ile nitelikli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="d4ab5-158">Aşağıdaki yapı (tablonun `a` `T`geçerli bir sütunu olduğunu varsayarak) Transact-SQL'de [!INCLUDE[esql](../../../../../../includes/esql-md.md)]geçerlidir, ancak .</span><span class="sxs-lookup"><span data-stu-id="d4ab5-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in Transact-SQL but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```sql  
SELECT a FROM T
```  
  
 <span data-ttu-id="d4ab5-159">Form, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4ab5-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```sql  
SELECT t.a AS A FROM T AS t
```  
  
 <span data-ttu-id="d4ab5-160">Tablo diğer adları `from` yan tümcede isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="d4ab5-161">Tablonun adı örtük takma ad olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-162">aşağıdaki formu da sağlar:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-162">allows the following form as well:</span></span>  
  
```sql  
SELET Tab.a FROM Tab
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="d4ab5-163">Nesneler arasında gezinme</span><span class="sxs-lookup"><span data-stu-id="d4ab5-163">Navigation Through Objects</span></span>  
 <span data-ttu-id="d4ab5-164">Transact-SQL, bir tablonun (bir satır) sütununa başvurmak için "." notasyonunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-164">Transact-SQL uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-165">bu gösterimi (programlama dillerinden ödünç alınan) bir nesnenin özellikleri arasında gezinmeyi desteklemek için genişletir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="d4ab5-166">Örneğin, Tür `p` Kişi bir ifade ise, aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu kişinin adresinin şehir başvurmak için sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```sql  
p.Address.City
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="d4ab5-167">Destek Yok \*</span><span class="sxs-lookup"><span data-stu-id="d4ab5-167">No Support for \*</span></span>  
 <span data-ttu-id="d4ab5-168">Transact-SQL, tüm satır için bir diğer ad olarak niteliksiz \* \* sözdizimini\*ve bu tablonun alanları için bir kısayol olarak nitelikli sözdizimini (t.) destekler.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-168">Transact-SQL supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="d4ab5-169">Buna ek olarak, Transact-SQL nulls içeren özel bir sayı ()\*toplam sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-169">In addition, Transact-SQL allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-170">\* yapıyı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-170">does not support the \* construct.</span></span> <span data-ttu-id="d4ab5-171">`select * from T` Formun Transact-SQL sorguları `select T1.* from T1, T2...` ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sırasıyla `select value t from T as t` `select value t1 from T1 as t1, T2 as t2...`ve olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-171">Transact-SQL queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="d4ab5-172">Ayrıca, bu yapılar devralmayı (değer ikame edilebilirliği) işlerken, `select *` varyantlar bildirilen türün üst düzey özellikleriyle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-173">`count(*)` toplamı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="d4ab5-174">Bunun yerine `count(0)` kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="d4ab5-175">Gruplandırmadeğişiklikleri</span><span class="sxs-lookup"><span data-stu-id="d4ab5-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-176">anahtarların diğer `group by` adlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="d4ab5-177">Yan tümce `select` ve `having` yan tümcedeki ifadeler, bu diğer adlar aracılığıyla `group by` anahtarlara başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="d4ab5-178">Örneğin, bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```sql  
SELECT k1, count(t.a), sum(t.a)
FROM T AS t
GROUP BY t.b + t.c AS k1
```  
  
 <span data-ttu-id="d4ab5-179">... aşağıdaki Transact-SQL'e eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-179">...is equivalent to the following Transact-SQL:</span></span>  
  
```sql  
SELECT b + c, count(*), sum(a)
FROM T
GROUP BY b + c
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="d4ab5-180">Koleksiyon Tabanlı Agregalar</span><span class="sxs-lookup"><span data-stu-id="d4ab5-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-181">iki tür agregayı destekler.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="d4ab5-182">Koleksiyon tabanlı agregalar koleksiyonlar üzerinde çalışır ve toplanan sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="d4ab5-183">Bunlar sorgunun herhangi bir yerinde görünebilir `group by` ve bir yan tümce gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="d4ab5-184">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-184">For example:</span></span>  
  
```sql  
SELECT t.a AS a, count({1,2,3}) AS b FROM T AS t
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-185">ayrıca SQL tarzı agregaları da destekler.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="d4ab5-186">Örnek:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-186">For example:</span></span>  
  
```sql  
SELECT a, sum(t.b) FROM T AS t GROUP BY t.a AS a
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="d4ab5-187">Madde Kullanımına GÖRE SİPARİş</span><span class="sxs-lookup"><span data-stu-id="d4ab5-187">ORDER BY Clause Usage</span></span>  
<span data-ttu-id="d4ab5-188">Transact-SQL `ORDER BY` yan tümcelerinin yalnızca en `SELECT .. FROM .. WHERE` üst blokta belirtilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-188">Transact-SQL allows `ORDER BY` clauses to be specified only in the topmost `SELECT .. FROM .. WHERE` block.</span></span> <span data-ttu-id="d4ab5-189">İç [!INCLUDE[esql](../../../../../../includes/esql-md.md)] içe bir `ORDER BY` ifade kullanabilirsiniz ve sorguda herhangi bir yere yerleştirilebilir, ancak iç içe bir sorguda sıralama korunmuyor.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-189">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested `ORDER BY` expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="d4ab5-190">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="d4ab5-190">Identifiers</span></span>  
 <span data-ttu-id="d4ab5-191">Transact-SQL'de tanımlayıcı karşılaştırması geçerli veritabanının harmanlamaını temel almaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-191">In Transact-SQL, identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="d4ab5-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], tanımlayıcılar her zaman duyarsız ve aksan duyarlı [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (yani, aksanlı ve aksansız karakterler arasında ayrım; örneğin, 'a' 'a' eşit değildir).</span><span class="sxs-lookup"><span data-stu-id="d4ab5-192">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-193">aynı görünen ancak farklı kod sayfalarından gelen harflerin sürümlerini farklı karakterler olarak ele alar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-193">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="d4ab5-194">Daha fazla bilgi için [Giriş Karakter Kümesi'ne](input-character-set-entity-sql.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-194">For more information, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="d4ab5-195">Transact-SQL İşlevselliği Entity SQL'de Kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="d4ab5-195">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="d4ab5-196">Aşağıdaki Transact-SQL işlevi [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d4ab5-196">The following Transact-SQL functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="d4ab5-197">Dml</span><span class="sxs-lookup"><span data-stu-id="d4ab5-197">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-198">şu anda DML deyimleri (ekleme, güncelleme, silme) için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-198">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="d4ab5-199">Ddl</span><span class="sxs-lookup"><span data-stu-id="d4ab5-199">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-200">geçerli sürümde DDL için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-200">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="d4ab5-201">Kesin Programlama Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="d4ab5-201">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-202">Transact-SQL'den farklı olarak zorunlu programlama için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-202">provides no support for imperative programming, unlike Transact-SQL.</span></span> <span data-ttu-id="d4ab5-203">Bunun yerine bir programlama dili kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-203">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="d4ab5-204">İşlevleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="d4ab5-204">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-205">henüz gruplandırma işlevleri (örneğin, CUBE, ROLLUP ve GROUPING_SET) için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-205">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="d4ab5-206">Analitik İşlevler</span><span class="sxs-lookup"><span data-stu-id="d4ab5-206">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-207">(henüz) analitik işlevler için destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-207">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="d4ab5-208">Dahili Fonksiyonlar, Operatörler</span><span class="sxs-lookup"><span data-stu-id="d4ab5-208">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-209">İşlevler ve işleçler içinde yerleşik Olan Transact-SQL'in bir alt kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-209">supports a subset of Transact-SQL's built in functions and operators.</span></span> <span data-ttu-id="d4ab5-210">Bu işleçler ve işlevler büyük mağaza sağlayıcıları tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-210">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-211">sağlayıcı bildiriminde beyan edilen mağazaya özgü işlevleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-211">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="d4ab5-212">Ayrıca, Varlık Çerçevesi, yerleşik ve kullanıcı tarafından tanımlanan varolan mağaza [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlevlerini kullanmak üzere beyan etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-212">Additionally, the Entity Framework allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="d4ab5-213">Ipuç -ları</span><span class="sxs-lookup"><span data-stu-id="d4ab5-213">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-214">sorgu ipuçları için mekanizmalar sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-214">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="d4ab5-215">Toplu İşlem Sorgu Sonuçları</span><span class="sxs-lookup"><span data-stu-id="d4ab5-215">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-216">toplu sorgu sonuçlarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-216">does not support batching query results.</span></span> <span data-ttu-id="d4ab5-217">Örneğin, aşağıdaki geçerli Transact-SQL (toplu iş olarak gönderme):</span><span class="sxs-lookup"><span data-stu-id="d4ab5-217">For example, the following is valid Transact-SQL (sending as a batch):</span></span>  
  
```sql  
SELECT * FROM products;
SELECT * FROM catagories;
```  
  
 <span data-ttu-id="d4ab5-218">Ancak, eşdeğeri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="d4ab5-218">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```sql  
SELECT value p FROM Products AS p;
SELECT value c FROM Categories AS c;
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="d4ab5-219">komut başına yalnızca bir sonuç üreten sorgu deyimini destekler.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-219">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ab5-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4ab5-220">See also</span></span>

- [<span data-ttu-id="d4ab5-221">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4ab5-221">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="d4ab5-222">Desteklenmeyen İfadeler</span><span class="sxs-lookup"><span data-stu-id="d4ab5-222">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)
