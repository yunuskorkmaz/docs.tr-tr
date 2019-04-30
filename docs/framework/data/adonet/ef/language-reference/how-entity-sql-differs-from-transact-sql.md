---
title: Entity SQL ile Transact-SQL Arasındaki Farklar
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: 75ce0b00962526b76ea9f4b9fdfb0d1e1e564cdc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774757"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="fc0f4-102">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="fc0f4-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="fc0f4-103">Bu konuda arasındaki farklar açıklanmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc0f4-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="fc0f4-104">Devralma ve ilişkiler desteği</span><span class="sxs-lookup"><span data-stu-id="fc0f4-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-105">doğrudan kavramsal varlık şemalarıyla çalışan ve devralma ve ilişkiler gibi kavramsal model özelliklerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-105">works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="fc0f4-106">Devralma ile çalışırken, genellikle üst örnekleri koleksiyonundan bir alt örneklerini seçmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="fc0f4-107">[Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) işlecinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (benzer şekilde `oftype` içinde C# dizileri) bu özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="fc0f4-108">Koleksiyonlar için destek</span><span class="sxs-lookup"><span data-stu-id="fc0f4-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-109">Koleksiyonlar, birinci sınıf varlıklar olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-109">treats collections as first-class entities.</span></span> <span data-ttu-id="fc0f4-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-110">For example:</span></span>  
  
- <span data-ttu-id="fc0f4-111">Koleksiyon ifadeleri geçerli bir `from` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-111">Collection expressions are valid in a `from` clause.</span></span>  
  
- <span data-ttu-id="fc0f4-112">`in` ve `exists` alt sorgular genelleştirilmiş koleksiyonlarınız izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="fc0f4-113">Alt sorgu koleksiyonu türüdür.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="fc0f4-114">`e1 in e2` ve `exists(e)` olan [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu işlemleri gerçekleştirmek için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
- <span data-ttu-id="fc0f4-115">Ayarlama işlemleri, gibi `union`, `intersect`, ve `except`, artık koleksiyonlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
- <span data-ttu-id="fc0f4-116">Birleştirmeler koleksiyonlarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="fc0f4-117">İfadeler için destek</span><span class="sxs-lookup"><span data-stu-id="fc0f4-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="fc0f4-118">alt sorgular (tablolar) ve ifadeleri (satırları ve sütunları) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-118">has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="fc0f4-119">Koleksiyonlar ve iç içe geçmiş koleksiyonlar desteklemek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] her şey bir ifade yapar.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-120">Daha fazla birleştirilebilir olan [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]— her ifade her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-120">is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="fc0f4-121">Sorgu ifadeleri her zaman öngörülen türleri koleksiyonlarında ve neden olabilir bir toplama ifadesi izin verilen her yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="fc0f4-122">Hakkında bilgi için [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] desteklenmeyen ifadeler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], bkz: [desteklenmeyen ifadeler](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fc0f4-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="fc0f4-123">Aşağıdaki tüm geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="fc0f4-124">Alt sorgular Tekdüzen adların kullanımı</span><span class="sxs-lookup"><span data-stu-id="fc0f4-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="fc0f4-125">Kendi Vurgu, tablolarda verilen [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgular bağlamsal yorumunu yapar.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="fc0f4-126">Örneğin, bir alt sorguda `from` yan tümcesi bir çoklu küme (tablo) olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="fc0f4-127">Ancak kullanılan aynı alt sorgu `select` yan tümcesi skaler bir alt sorgu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="fc0f4-128">Benzer şekilde, sol tarafında kullanılan alt sorgu bir `in` işleci, skaler bir alt sorgu sağ tarafındaki multiset alt sorgu beklenmektedir sırada olacak şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-129">Bu farklar ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-129">eliminates these differences.</span></span> <span data-ttu-id="fc0f4-130">Bir ifade içinde kullanıldığı bağlamda benzemez Tekdüzen bir yorumu vardır.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-131">multiset alt sorgular olması için tüm alt sorgulara göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-131">considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="fc0f4-132">Skaler değer Alt sorgudan isteniyorsa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sağlar `anyelement` işleci (Bu durumda, alt) bir koleksiyon üzerinde çalışır ve koleksiyondan bir singleton değeri ayıklar.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="fc0f4-133">Alt sorgular için örtük zorlamayı kaçınma</span><span class="sxs-lookup"><span data-stu-id="fc0f4-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="fc0f4-134">İlgili bir yan etkisi Tekdüzen değerlendirilmesi, alt sorgularda, alt sorgularda örtük dönüştürülmesi için skaler değerler ' dir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="fc0f4-135">Özellikle de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], bir çoklu küme satır (tek bir alan ile) bir skaler değerin veri türü olan alanın örtük olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-136">Bu örtük zorlama desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-136">does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-137">tekil değer bir koleksiyondan ayıklanacak ANYELEMENT işleci sağlar ve bir `select value` yan tümcesi bir sorgu ifadesinde sırasında satır sarmalayıcı oluşturmaktan kaçınmak için.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-137">provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="fc0f4-138">Değer seçin: Örtük satır sarmalayıcı kaçınma</span><span class="sxs-lookup"><span data-stu-id="fc0f4-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="fc0f4-139">Select yan tümcesinde bir [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgu yan tümcesinde örtük olarak bir satır funcınner çevresindeki öğeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="fc0f4-140">Bu, skalerler nesneleri ve koleksiyonları oluşturamıyoruz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="fc0f4-141">bir alan bir rowtype ve aynı veri türünde bir tekil değer arasında örtük bir zorlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-141">allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-142">sağlar `select value` yan tümcesi örtük satır oluşturma atlanacak.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-142">provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="fc0f4-143">Yalnızca bir öğe belirtilebilir bir `select value` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="fc0f4-144">Böyle bir yan tümcesi kullanıldığında, öğeler etrafında hiçbir satır sarmalayıcı oluşturulur `select` yan tümcesi ve istediğiniz şekle koleksiyonunu oluşturulur, örneğin: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-145">row oluşturucusunda rastgele satırları oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-145">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="fc0f4-146">`select` projeksiyon bir veya daha fazla öğeleri ve sonuçları bir veri kayıttaki alanları ile aşağıdaki gibi alır:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="fc0f4-147">Sol bağıntı ve diğer ad kullanımı</span><span class="sxs-lookup"><span data-stu-id="fc0f4-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="fc0f4-148">İçinde [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], belirli bir kapsamda ifadeleri (tek bir yan tümce ister `select` veya `from`) ifadeler aynı kapsam içinde daha önce tanımlanan başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="fc0f4-149">Bazı SQL larımızın (dahil olmak üzere [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) bunların sınırlı forms desteği `from` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-150">içinde sol bağıntılar genelleştirir `from` yan tümcesi ve aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-150">generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="fc0f4-151">İfadelerde `from` yan tümcesi aynı yan ek söz dizimi gerek kalmadan eski tanımları (sol tanımları) başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-152">Ayrıca sorguları ilgili ek kısıtlamalar getirir `group by` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-152">also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="fc0f4-153">İfadelerde `select` yan tümcesi ve `having` gibi sorguların yan tümcesi için yalnızca başvurabilir `group by` diğer adlarını aracılığıyla anahtarları.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="fc0f4-154">Şu yapı geçersiz [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] ancak yer almayan [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="fc0f4-155">Bunu yapmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="fc0f4-156">Başvuru tabloları (koleksiyonlar) sütunları (özellikleri)</span><span class="sxs-lookup"><span data-stu-id="fc0f4-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="fc0f4-157">Sütun başvurularının tümü [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tablo diğer adıyla nitelendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="fc0f4-158">Şu yapı (varsayarak `a` geçerli bir sütun tablonun `T`) geçersiz [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] fakat [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc0f4-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="fc0f4-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formu</span><span class="sxs-lookup"><span data-stu-id="fc0f4-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="fc0f4-160">Tablo diğer adları isteğe bağlı olarak `from` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="fc0f4-161">Tablonun adını örtük diğer ad olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-162">Aşağıdaki biçimi de sağlar:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-162">allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="fc0f4-163">Nesneler aracılığıyla gezinme</span><span class="sxs-lookup"><span data-stu-id="fc0f4-163">Navigation Through Objects</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="fc0f4-164">kullanır "." gösterimi sütunları (satırının) başvuru için bir tablo.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-164">uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-165">bir nesnenin özelliklerini gezinmeyi desteklemek için bu gösterim (programlama dillerinden ödünç) genişletir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-165">extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="fc0f4-166">Örneğin, varsa `p` olduğundan bir ifade yazın kişi, aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] adresi bu kişinin şehrini başvuran söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="fc0f4-167">Desteği \*</span><span class="sxs-lookup"><span data-stu-id="fc0f4-167">No Support for \*</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="fc0f4-168">Nitelenmemiş destekler \* sözdizimi için tüm bir satırda ve tam bir diğer ad olarak \* sözdizimi (t\*) söz konusu tablonun alanlar için bir kısayol olarak.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-168">supports the unqualified \* syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="fc0f4-169">Ayrıca, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] özel sayısını sağlar (\*) null değerler içeren bir toplama.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-170">desteklemediği \* yapısı.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-170">does not support the \* construct.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="fc0f4-171">Formun sorguları `select * from T` ve `select T1.* from T1, T2...` ifade edilebilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak `select value t from T as t` ve `select value t1 from T1 as t1, T2 as t2...`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-171">queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="fc0f4-172">Ayrıca, bu yapıları devralma (değer substitutability) işleme sırasında `select *` çeşitleri bildirilen türü için üst düzey özelliklerini kısıtlı.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-173">desteklemediği `count(*)` toplama.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-173">does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="fc0f4-174">Bunun yerine `count(0)` kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="fc0f4-175">Gruplama Ölçütü değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="fc0f4-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-176">diğer ad kullanımı, destekler `group by` anahtarları.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-176">supports aliasing of `group by` keys.</span></span> <span data-ttu-id="fc0f4-177">İfadelerde `select` yan tümcesi ve `having` yan tümcesi başvurmalıdır `group by` anahtarlarında bu diğer adları.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="fc0f4-178">Örneğin, bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] söz dizimi:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="fc0f4-179">.. belirtiminde aşağıdaki eşdeğer [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="fc0f4-180">Koleksiyon tabanlı toplamaları</span><span class="sxs-lookup"><span data-stu-id="fc0f4-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-181">iki tür toplamlar destekler.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-181">supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="fc0f4-182">Koleksiyon tabanlı toplamlar koleksiyonlarda çalışır ve toplanan sonucu.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="fc0f4-183">Bu sorguda her yerde görünebilir ve gerekli olmayan bir `group by` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="fc0f4-184">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-185">Ayrıca SQL stili toplamalar destekler.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-185">also supports SQL-style aggregates.</span></span> <span data-ttu-id="fc0f4-186">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="fc0f4-187">ORDER BY yan tümcesi kullanımı</span><span class="sxs-lookup"><span data-stu-id="fc0f4-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="fc0f4-188">yalnızca üstteki Seç belirtilmesi ORDER BY yan tümcesi sağlar...</span><span class="sxs-lookup"><span data-stu-id="fc0f4-188">allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="fc0f4-189">KAYNAK..</span><span class="sxs-lookup"><span data-stu-id="fc0f4-189">FROM ..</span></span> <span data-ttu-id="fc0f4-190">Burada engelleyin.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-190">WHERE block.</span></span> <span data-ttu-id="fc0f4-191">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iç içe geçmiş bir ORDER BY deyimi kullanabilirsiniz ve her yerde sorguda yerleştirilebilir, ancak iç içe geçmiş bir sorgusunda sıralama korunur.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="fc0f4-192">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="fc0f4-192">Identifiers</span></span>  
 <span data-ttu-id="fc0f4-193">İçinde [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], tanımlayıcı karşılaştırmasına geçerli veritabanı harmanlaması üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="fc0f4-194">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)], tanımlayıcılar her zaman büyük/küçük harfe duyarsızdır ve aksan duyarlı (diğer bir deyişle, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayıran karakter vurgulanmış ve vurgulanmamış; Örneğin, 'bir' 'ấ için' eşit değildir).</span><span class="sxs-lookup"><span data-stu-id="fc0f4-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-195">aynı görünür, ancak farklı bir karakter olarak farklı kod sayfalarından olan harf sürümleri değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-195">treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="fc0f4-196">Daha fazla bilgi için [giriş karakter kümesi](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fc0f4-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="fc0f4-197">Transact-SQL işlevleri varlık SQL kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="fc0f4-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="fc0f4-198">Aşağıdaki [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] işlevselliği kullanılabilir değil [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc0f4-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="fc0f4-199">DML</span><span class="sxs-lookup"><span data-stu-id="fc0f4-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-200">şu anda DML deyimleri için destek sağlar (ekleme, güncelleştirme ve silme).</span><span class="sxs-lookup"><span data-stu-id="fc0f4-200">currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="fc0f4-201">DDL</span><span class="sxs-lookup"><span data-stu-id="fc0f4-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-202">geçerli sürümünde DDL desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-202">provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="fc0f4-203">Kesin Programlama Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="fc0f4-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-204">aksine kesin programlama için destek sağlar [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc0f4-204">provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fc0f4-205">Bunun yerine bir programlama dili kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="fc0f4-206">İşlevleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="fc0f4-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-207">henüz destek işlevleri (örneğin, CUBE, ROLLUP ve GROUPING_SET) gruplandırma için sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-207">does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="fc0f4-208">Analitik İşlevler</span><span class="sxs-lookup"><span data-stu-id="fc0f4-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-209">yok (henüz) analitik işlevler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-209">does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="fc0f4-210">Yerleşik işlevleri, işleçler</span><span class="sxs-lookup"><span data-stu-id="fc0f4-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-211">bir alt kümesini destekler [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]işlevler ve işleçler yerleşik.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-211">supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="fc0f4-212">Bu işleç ve işlevlerini büyük depolama sağlayıcıları tarafından desteklenmesi olasılığı düşüktür.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-213">Sağlayıcı bildiriminde belirtilen depolama özgü işlevleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-213">uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="fc0f4-214">Ayrıca, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] yerleşik bildirmek olanak tanır ve var olan kullanıcı tanımlı deposuna İşlevler, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="fc0f4-215">İpuçları</span><span class="sxs-lookup"><span data-stu-id="fc0f4-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-216">Sorgu ipuçları mekanizmalar sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-216">does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="fc0f4-217">Sorgu sonuçları toplu işleme</span><span class="sxs-lookup"><span data-stu-id="fc0f4-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-218">Toplu işlem sorgu sonuçları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-218">does not support batching query results.</span></span> <span data-ttu-id="fc0f4-219">Örneğin, aşağıdaki geçerli [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (toplu iş olarak gönderme):</span><span class="sxs-lookup"><span data-stu-id="fc0f4-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="fc0f4-220">Ancak, eşdeğer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenmiyor:</span><span class="sxs-lookup"><span data-stu-id="fc0f4-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc0f4-221">Yalnızca komut başına bir sonuç oluşturmayı sorgu deyimini destekler.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-221">only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0f4-222">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc0f4-222">See also</span></span>

- [<span data-ttu-id="fc0f4-223">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fc0f4-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="fc0f4-224">Desteklenmeyen İfadeler</span><span class="sxs-lookup"><span data-stu-id="fc0f4-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
