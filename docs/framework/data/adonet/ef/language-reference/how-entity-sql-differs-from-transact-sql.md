---
title: "Varlık SQL Transact-SQL nasıl farklıdır"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3f80ec1ac51dded1f91d1a18c4d4e24836cf92cd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="37c89-102">Varlık SQL Transact-SQL nasıl farklıdır</span><span class="sxs-lookup"><span data-stu-id="37c89-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="37c89-103">Bu konuda arasındaki farklar açıklanmaktadır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37c89-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="37c89-104">Devralma ve ilişkileri desteği</span><span class="sxs-lookup"><span data-stu-id="37c89-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-105">doğrudan kavramsal varlık şemalarda çalışır ve devralma ve ilişkileri gibi kavramsal model özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="37c89-105"> works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="37c89-106">Devralma ile çalışırken, genellikle bir alt örnekleri üst örnekleri koleksiyonundan seçmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="37c89-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="37c89-107">[Oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) işlecinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (benzer şekilde `oftype` C# serileri) bu yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="37c89-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="37c89-108">Koleksiyonlar için destek</span><span class="sxs-lookup"><span data-stu-id="37c89-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-109">koleksiyonları birinci sınıf varlıklar olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="37c89-109"> treats collections as first-class entities.</span></span> <span data-ttu-id="37c89-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="37c89-110">For example:</span></span>  
  
-   <span data-ttu-id="37c89-111">Koleksiyon ifadelerini geçerli bir `from` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="37c89-111">Collection expressions are valid in a `from` clause.</span></span>  
  
-   <span data-ttu-id="37c89-112">`in`ve `exists` alt sorgulara genelleştirilmiş herhangi bir koleksiyonu izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="37c89-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="37c89-113">Bir alt sorgu koleksiyon türüdür.</span><span class="sxs-lookup"><span data-stu-id="37c89-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="37c89-114">`e1 in e2`ve `exists(e)` olan [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu işlemleri gerçekleştirmek için yapıları.</span><span class="sxs-lookup"><span data-stu-id="37c89-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
-   <span data-ttu-id="37c89-115">Ayarlama işlemleri, aşağıdaki gibi `union`, `intersect`, ve `except`, şimdi koleksiyonlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="37c89-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
-   <span data-ttu-id="37c89-116">Birleştirmeler koleksiyonlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="37c89-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="37c89-117">İfadeler için destek</span><span class="sxs-lookup"><span data-stu-id="37c89-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="37c89-118">alt sorgular (tablolar) ve ifadeler (satırları ve sütunları) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="37c89-118"> has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="37c89-119">Koleksiyonlar ve iç içe geçmiş koleksiyonları desteklemek için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir ifade her şeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="37c89-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-120">Daha fazla birleştirilebilir [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]— her ifade herhangi bir kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37c89-120"> is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="37c89-121">Sorgu ifadeleri her zaman öngörülen türleri koleksiyonlarda ve neden olabilir bir toplama ifadesi kullanılabilir, herhangi bir yerde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37c89-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="37c89-122">Hakkında bilgi için [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] desteklenmez ifadeler [!INCLUDE[esql](../../../../../../includes/esql-md.md)], bkz: [desteklenmeyen ifadeler](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="37c89-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="37c89-123">Aşağıdaki tüm geçerli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular:</span><span class="sxs-lookup"><span data-stu-id="37c89-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="37c89-124">Alt sorgular Tekdüzen işlenmesi</span><span class="sxs-lookup"><span data-stu-id="37c89-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="37c89-125">Kendi Vurgu tablolarda, verilen [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgulara bağlamsal yorumu gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="37c89-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="37c89-126">Örneğin, bir alt sorguda `from` yan tümcesi multiset (tablo) olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="37c89-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="37c89-127">Ancak kullanılan aynı alt sorgu `select` yan tümcesi, skaler bir alt sorgu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="37c89-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="37c89-128">Benzer şekilde, sol tarafında kullanılan alt sorgu bir `in` işleci sağ tarafında çok kümeli bir alt sorgu beklenmektedir sırada skaler bir alt sorgu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="37c89-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-129">Bu farklılıklar ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="37c89-129"> eliminates these differences.</span></span> <span data-ttu-id="37c89-130">Bir ifade, kullanıldığı bağlamda bağlı olmayan bir Tekdüzen yorumlama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="37c89-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-131">çok kümeli alt sorgulara olması için tüm alt sorgulara göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="37c89-131"> considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="37c89-132">Alt sorgudan bir skaler değere isterseniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sağlar `anyelement` koleksiyonu (Bu durumda, alt sorgu) üzerinde çalışır ve bir tek değer koleksiyondan ayıklar işleci.</span><span class="sxs-lookup"><span data-stu-id="37c89-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="37c89-133">Alt sorgular için örtük zorlamayı önleme</span><span class="sxs-lookup"><span data-stu-id="37c89-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="37c89-134">Alt sorgular Tekdüzen işlenmesi ilgili yan etkisi skaler değerler alt sorgulara örtük dönüştürme ' dir.</span><span class="sxs-lookup"><span data-stu-id="37c89-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="37c89-135">Özellikle [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], multiset (ile tek bir alan) satır örtük veri türü olan alanın bir skaler değerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="37c89-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-136">Bu örtük zorlama desteklemez.</span><span class="sxs-lookup"><span data-stu-id="37c89-136"> does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-137">singleton değeri bir koleksiyondan çıkarmak için ANYELEMENT işleci sağlar ve bir `select value` bir sorgu ifadesi sırasında satır sarmalayıcı oluşturmamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="37c89-137"> provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="37c89-138">Seçme değerini: örtük satır sarmalayıcı önleme</span><span class="sxs-lookup"><span data-stu-id="37c89-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="37c89-139">Select yan tümcesinde bir [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] alt sorgu yan tümcesinde örtük olarak bir satır sarmalayıcı öğelerin çevresindeki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37c89-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="37c89-140">Bu, skalerler veya nesneler koleksiyonları oluşturamıyoruz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="37c89-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="37c89-141">rowtype bir alan ve aynı veri türünde bir tek değer arasında örtük bir zorlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="37c89-141"> allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-142">sağlar `select value` örtük satır yapım atlamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="37c89-142"> provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="37c89-143">Yalnızca bir öğe belirtilebilir bir `select value` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="37c89-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="37c89-144">Bu tür bir yan tümcesi kullanıldığında, hiçbir satır sarmalayıcı öğeleri geçici oluşturulan `select` yan tümcesi ve istediğiniz şekli koleksiyonu üretilebilir, örneğin: `select value a`.</span><span class="sxs-lookup"><span data-stu-id="37c89-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-145">row Oluşturucusu rasgele satırları oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="37c89-145"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="37c89-146">`select`projeksiyon bir veya daha fazla öğe ve sonuçları bir veri kaydındaki alanları ile aşağıdaki gibi alır:</span><span class="sxs-lookup"><span data-stu-id="37c89-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="37c89-147">Sol bağıntı ve diğer ad</span><span class="sxs-lookup"><span data-stu-id="37c89-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="37c89-148">İçinde [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], belirli bir kapsamda ifadeleri (tek bir yan tümce ister `select` veya `from`) daha önce aynı kapsamda tanımlanan ifadeleri başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="37c89-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="37c89-149">Bazı Portekizce Lehçesi SQL (de dahil olmak üzere [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) biri ile sınırlı forms desteği `from` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="37c89-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-150">içinde sol bağıntıları genelleştirir `from` yan tümcesi ve aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="37c89-150"> generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="37c89-151">İfadelerde `from` yan tümcesi başvuru önceki tanımları (sol tanımları) ek sözdizimi gerek kalmadan aynı yan tümcesinde.</span><span class="sxs-lookup"><span data-stu-id="37c89-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-152">Ayrıca sorguları ilgili ek kısıtlamalar getirir `group by` yan tümceleri.</span><span class="sxs-lookup"><span data-stu-id="37c89-152"> also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="37c89-153">İfadelerde `select` yan tümcesi ve `having` sorgularını yan tümcesi yalnızca başvurabilir `group by` benzersizse anahtarlarında.</span><span class="sxs-lookup"><span data-stu-id="37c89-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="37c89-154">Şu yapı geçersiz [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] ancak bulunmayan [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="37c89-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="37c89-155">Bunu yapmak için [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="37c89-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="37c89-156">Başvuruda bulunan sütunlar (Özellikler) tabloları (koleksiyonu)</span><span class="sxs-lookup"><span data-stu-id="37c89-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="37c89-157">Tüm sütun başvuruları [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tablo diğer ad ile nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="37c89-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="37c89-158">Şu yapı (varsayılarak `a` geçerli bir sütun tablonun `T`) geçersiz [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37c89-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="37c89-159">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Formu</span><span class="sxs-lookup"><span data-stu-id="37c89-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="37c89-160">Tablo diğer adları isteğe bağlı olarak `from` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="37c89-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="37c89-161">Tablonun adını örtük diğer ad olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37c89-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-162">Aşağıdaki form de sağlar:</span><span class="sxs-lookup"><span data-stu-id="37c89-162"> allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="37c89-163">Nesneleri gezinmeyi</span><span class="sxs-lookup"><span data-stu-id="37c89-163">Navigation Through Objects</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="37c89-164">kullanır "." (bir satırı) sütunlarının başvuran gösterimi bir tablo.</span><span class="sxs-lookup"><span data-stu-id="37c89-164"> uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-165">bir nesnenin özelliklerini gezinmeyi desteklemek için bu gösterim (programlama dilleri ödünç) genişletir.</span><span class="sxs-lookup"><span data-stu-id="37c89-165"> extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="37c89-166">Örneğin, varsa `p` olan bir ifadenin türünü kişi, aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu kişinin adresini Şehir başvuran söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="37c89-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="37c89-167">Desteği \*</span><span class="sxs-lookup"><span data-stu-id="37c89-167">No Support for \*</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="37c89-168">Nitelenmemiş destekleyen \* sözdizimi tüm satır ve tam bir diğer ad olarak \\* sözdizimi (t.\\*) bu tabloyu alanlar için bir kısayol olarak.</span><span class="sxs-lookup"><span data-stu-id="37c89-168"> supports the unqualified \* syntax as an alias for the entire row, and the qualified \\* syntax (t.\\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="37c89-169">Ayrıca, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] için özel bir sayı verir (\\*) null değerler içeren toplama.</span><span class="sxs-lookup"><span data-stu-id="37c89-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-170">desteklemediği \* yapısı.</span><span class="sxs-lookup"><span data-stu-id="37c89-170"> does not support the \* construct.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="37c89-171">formu sorguları `select * from T` ve `select T1.* from T1, T2...` ifade edilebilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak `select value t from T as t` ve `select value t1 from T1 as t1, T2 as t2...`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="37c89-171"> queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="37c89-172">Ek olarak, bu yapıları devralma (değer substitutability) işleme sırasında `select *` çeşitleri bildirilen en üst düzey özelliklerini kısıtlı.</span><span class="sxs-lookup"><span data-stu-id="37c89-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-173">desteklemediği `count(*)` toplama.</span><span class="sxs-lookup"><span data-stu-id="37c89-173"> does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="37c89-174">Bunun yerine `count(0)` kullanın.</span><span class="sxs-lookup"><span data-stu-id="37c89-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="37c89-175">Grup tarafından yapılan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="37c89-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-176">diğer ad olarak destekleyen `group by` anahtarları.</span><span class="sxs-lookup"><span data-stu-id="37c89-176"> supports aliasing of `group by` keys.</span></span> <span data-ttu-id="37c89-177">İfadelerde `select` yan tümcesi ve `having` yan tümcesi başvurmalıdır `group by` bu diğer adları anahtarlarında.</span><span class="sxs-lookup"><span data-stu-id="37c89-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="37c89-178">Örneğin, bu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sözdizimi:</span><span class="sxs-lookup"><span data-stu-id="37c89-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="37c89-179">.. belirtiminde aşağıdaki eşdeğer [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="37c89-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="37c89-180">Koleksiyon tabanlı toplar</span><span class="sxs-lookup"><span data-stu-id="37c89-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-181">iki tür toplamalar destekler.</span><span class="sxs-lookup"><span data-stu-id="37c89-181"> supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="37c89-182">Koleksiyon tabanlı toplamalar koleksiyonlar üzerinde çalışır ve toplanan sonucu.</span><span class="sxs-lookup"><span data-stu-id="37c89-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="37c89-183">Bu sorguda herhangi bir yerde görünebilir ve gerekli olmadığı bir `group by` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="37c89-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="37c89-184">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="37c89-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-185">Ayrıca SQL stili toplamalar destekler.</span><span class="sxs-lookup"><span data-stu-id="37c89-185"> also supports SQL-style aggregates.</span></span> <span data-ttu-id="37c89-186">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="37c89-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="37c89-187">ORDER BY yan tümcesi kullanımı</span><span class="sxs-lookup"><span data-stu-id="37c89-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="37c89-188">yalnızca en üstteki Seç belirtilmesini ORDER BY yan tümceleri sağlar...</span><span class="sxs-lookup"><span data-stu-id="37c89-188"> allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="37c89-189">KAYNAK..</span><span class="sxs-lookup"><span data-stu-id="37c89-189">FROM ..</span></span> <span data-ttu-id="37c89-190">Burada engelleyin.</span><span class="sxs-lookup"><span data-stu-id="37c89-190">WHERE block.</span></span> <span data-ttu-id="37c89-191">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] iç içe geçmiş bir ORDER BY ifadesi kullanabilirsiniz ve her yerden sorguda yerleştirilebilir, ancak iç içe bir sorgu sıralama korunur.</span><span class="sxs-lookup"><span data-stu-id="37c89-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
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
  
## <a name="identifiers"></a><span data-ttu-id="37c89-192">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="37c89-192">Identifiers</span></span>  
 <span data-ttu-id="37c89-193">İçinde [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], tanımlayıcı karşılaştırma geçerli veritabanı harmanlamasının dayanır.</span><span class="sxs-lookup"><span data-stu-id="37c89-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="37c89-194">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)], tanımlayıcıları her zaman büyük küçük harfe duyarlı ve aksan duyarlı (diğer bir deyişle, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayırt vurgulanmış ve olarak karakter arasında; Örneğin, 'bir' 'ấ' eşit değildir).</span><span class="sxs-lookup"><span data-stu-id="37c89-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-195">aynı görünür, ancak farklı karakter olarak farklı kod sayfalarından olan harf sürümlerini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="37c89-195"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="37c89-196">Daha fazla bilgi için bkz: [giriş karakter kümesi](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="37c89-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="37c89-197">Transact-SQL işlevsellik varlık SQL yok</span><span class="sxs-lookup"><span data-stu-id="37c89-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="37c89-198">Aşağıdaki [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] işlevselliği kullanılabilir değil [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37c89-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="37c89-199">DML</span><span class="sxs-lookup"><span data-stu-id="37c89-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-200">şu anda DML deyimleri için destek sağlar (Ekle, Güncelleştir, Sil).</span><span class="sxs-lookup"><span data-stu-id="37c89-200"> currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="37c89-201">DDL</span><span class="sxs-lookup"><span data-stu-id="37c89-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-202">Geçerli sürümde DDL desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="37c89-202"> provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="37c89-203">Kesinlik temelli programlama</span><span class="sxs-lookup"><span data-stu-id="37c89-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-204">aksine kesinlik temelli programlama için destek sağlar [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37c89-204"> provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="37c89-205">Bunun yerine bir programlama dili kullanın.</span><span class="sxs-lookup"><span data-stu-id="37c89-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="37c89-206">İşlevleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="37c89-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-207">henüz destek işlevleri (örneğin, CUBE, ROLLUP ve GROUPING_SET) gruplandırmak için sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="37c89-207"> does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="37c89-208">Analitik İşlevler</span><span class="sxs-lookup"><span data-stu-id="37c89-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-209">yok (henüz) analitik işlevler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="37c89-209"> does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="37c89-210">Yerleşik İşlevler, işleçler</span><span class="sxs-lookup"><span data-stu-id="37c89-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-211">bir alt kümesini destekler [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]yerleşik işlevler ve işleçler.</span><span class="sxs-lookup"><span data-stu-id="37c89-211"> supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="37c89-212">Bu işleçler ve İşlevler temel depolama sağlayıcıları tarafından desteklenen olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="37c89-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-213">Sağlayıcı bildiriminde bildirilen deposu özgü işlevlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="37c89-213"> uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="37c89-214">Ayrıca, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] yerleşik bildirmek sağlar ve kullanıcı tanımlı varolan depolama işlevleri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="37c89-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="37c89-215">İpuçları</span><span class="sxs-lookup"><span data-stu-id="37c89-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-216">Sorgu ipuçları için mekanizmaları sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="37c89-216"> does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="37c89-217">Sorgu sonuçları toplu işleme</span><span class="sxs-lookup"><span data-stu-id="37c89-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-218">Toplu sorgu sonuçları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="37c89-218"> does not support batching query results.</span></span> <span data-ttu-id="37c89-219">Örneğin, aşağıdaki geçerli [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (toplu iş olarak gönderme):</span><span class="sxs-lookup"><span data-stu-id="37c89-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="37c89-220">Ancak, eşdeğer [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenmiyor:</span><span class="sxs-lookup"><span data-stu-id="37c89-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="37c89-221">yalnızca komutu her bir sonuç oluşturan sorgu deyimini destekler.</span><span class="sxs-lookup"><span data-stu-id="37c89-221"> only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c89-222">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37c89-222">See Also</span></span>  
 [<span data-ttu-id="37c89-223">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="37c89-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="37c89-224">Desteklenmeyen İfadeler</span><span class="sxs-lookup"><span data-stu-id="37c89-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
