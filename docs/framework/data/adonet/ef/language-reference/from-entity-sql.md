---
title: (Varlıktan, SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: de2ad24e5c6399ed1ca91e3907da4a66c056e337
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="from-entity-sql"></a><span data-ttu-id="e8b07-102">(Varlıktan, SQL)</span><span class="sxs-lookup"><span data-stu-id="e8b07-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="e8b07-103">Kullanılan koleksiyon belirtir [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="e8b07-103">Specifies the collection used in [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8b07-104">Syntax</span></span>  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a><span data-ttu-id="e8b07-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e8b07-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e8b07-106">Bir kaynak olarak kullanılacak bir koleksiyon verir herhangi bir geçerli sorgu ifade bir `SELECT` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e8b07-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8b07-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8b07-107">Remarks</span></span>  
 <span data-ttu-id="e8b07-108">A `FROM` yan tümcesi olan bir veya daha fazla virgülle ayrılmış bir liste `FROM` yan tümcesi öğeleri.</span><span class="sxs-lookup"><span data-stu-id="e8b07-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="e8b07-109">`FROM` Yan tümcesi için bir veya daha fazla kaynakları belirtmek için kullanılabilir bir `SELECT` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e8b07-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="e8b07-110">En basit biçimi bir `FROM` yan tümcesi bir toplama ve kaynağı olarak kullanılan bir diğer ad tanımlayan bir ifadedir tek bir sorgu bir `SELECT` deyimi, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="e8b07-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a><span data-ttu-id="e8b07-111">Yan tümcesi öğeleri</span><span class="sxs-lookup"><span data-stu-id="e8b07-111">FROM Clause Items</span></span>  
 <span data-ttu-id="e8b07-112">Her `FROM` yan tümce öğesi, bir kaynak koleksiyondaki başvurduğu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="e8b07-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e8b07-113"> Aşağıdaki sınıflarını destekleyen `FROM` yan tümcesi öğeleri: basit `FROM` yan tümcesi öğeleri `JOIN FROM` yan tümcesi öğeleri ve `APPLY FROM` yan tümcesi öğeleri.</span><span class="sxs-lookup"><span data-stu-id="e8b07-113"> supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="e8b07-114">Bunların her biri `FROM` yan tümcesi öğeleri aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8b07-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>  
  
### <a name="simple-from-clause-item"></a><span data-ttu-id="e8b07-115">Basit yan tümce öğesi</span><span class="sxs-lookup"><span data-stu-id="e8b07-115">Simple FROM Clause Item</span></span>  
 <span data-ttu-id="e8b07-116">En basit `FROM` yan tümce öğesi olan bir koleksiyonu ve bir diğer ad tanımlayan tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="e8b07-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="e8b07-117">İfade, yalnızca bir varlık kümesi veya alt sorgu veya koleksiyon türü herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8b07-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="e8b07-118">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e8b07-118">The following is an example:</span></span>  
  
```  
LOB.Customers as c  
```  
  
 <span data-ttu-id="e8b07-119">Diğer ad belirtimi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e8b07-119">The alias specification is optional.</span></span> <span data-ttu-id="e8b07-120">Yukarıdaki yan tümcesi öğesinden bir alternatif belirtimi şu olabilir:</span><span class="sxs-lookup"><span data-stu-id="e8b07-120">An alternate specification of the above from clause item could be the following:</span></span>  
  
```  
LOB.Customers  
```  
  
 <span data-ttu-id="e8b07-121">Diğer ad belirtilmezse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Toplama ifadesi temelinde bir diğer ad oluşturmak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8b07-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>  
  
### <a name="join-from-clause-item"></a><span data-ttu-id="e8b07-122">Yan tümcesi öğesinden katılma</span><span class="sxs-lookup"><span data-stu-id="e8b07-122">JOIN FROM Clause Item</span></span>  
 <span data-ttu-id="e8b07-123">A `JOIN FROM` yan tümce öğesi temsil eden iki arasında bir birleşim `FROM` yan tümcesi öğeleri.</span><span class="sxs-lookup"><span data-stu-id="e8b07-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e8b07-124"> destekler, birleşimler, İç birleşimler sol ve sağ dış birleşimler ve tam dış birleştirmeler arası.</span><span class="sxs-lookup"><span data-stu-id="e8b07-124"> supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="e8b07-125">Bu birleştirmeler benzer şekilde, desteklenen desteklenen [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8b07-125">All these joins are supported similar to the way that they are supported in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e8b07-126">Olarak [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], iki `FROM` yan tümcesi öğeleri söz konusu `JOIN` bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8b07-126">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="e8b07-127">Diğer bir deyişle, bunlar ilişkilendirilemez.</span><span class="sxs-lookup"><span data-stu-id="e8b07-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="e8b07-128">A `CROSS APPLY` veya `OUTER APPLY` bu durumlar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8b07-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>  
  
#### <a name="cross-joins"></a><span data-ttu-id="e8b07-129">Birleştirmeler arası</span><span class="sxs-lookup"><span data-stu-id="e8b07-129">Cross Joins</span></span>  
 <span data-ttu-id="e8b07-130">A `CROSS JOIN` sorgu ifadesi aşağıdaki örnekte gösterildiği gibi iki koleksiyonların Kartezyen ürün oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e8b07-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a><span data-ttu-id="e8b07-131">İç birleşimler</span><span class="sxs-lookup"><span data-stu-id="e8b07-131">Inner Joins</span></span>  
 <span data-ttu-id="e8b07-132">Bir `INNER JOIN` aşağıdaki örnekte gösterildiği gibi iki koleksiyon, kısıtlı bir Kartezyen ürün oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e8b07-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 <span data-ttu-id="e8b07-133">Önceki sorgu ifadesi her öğenin sağdaki nerede koleksiyonda her öğenin karşı eşleştirilmiş soldaki koleksiyonunun bileşimini işler `ON` koşul doğrudur.</span><span class="sxs-lookup"><span data-stu-id="e8b07-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="e8b07-134">Öyle değilse `ON` koşulu belirtilirse, bir `INNER JOIN` için eğrisi bir `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="e8b07-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="e8b07-135">Sol dış birleştirmeler ve sağ dış birleşimler</span><span class="sxs-lookup"><span data-stu-id="e8b07-135">Left Outer Joins and Right Outer Joins</span></span>  
 <span data-ttu-id="e8b07-136">Bir `OUTER JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonları, kısıtlı bir Kartezyen ürün oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e8b07-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="e8b07-137">Önceki sorgu ifadesi her öğenin sağdaki nerede koleksiyonda her öğenin karşı eşleştirilmiş soldaki koleksiyonunun bileşimini işler `ON` koşul doğrudur.</span><span class="sxs-lookup"><span data-stu-id="e8b07-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="e8b07-138">Varsa `ON` koşul yanlış ise, ifade hala soldaki null değerine sahip sağdaki öğesi karşı eşleştirilmiş öğesinde tek bir örneğini işler.</span><span class="sxs-lookup"><span data-stu-id="e8b07-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>  
  
 <span data-ttu-id="e8b07-139">A `RIGHT OUTER JOIN` benzer bir şekilde ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e8b07-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>  
  
#### <a name="full-outer-joins"></a><span data-ttu-id="e8b07-140">Tam dış birleşimler</span><span class="sxs-lookup"><span data-stu-id="e8b07-140">Full Outer Joins</span></span>  
 <span data-ttu-id="e8b07-141">Açık bir `FULL OUTER JOIN` aşağıdaki örnekte gösterildiği gibi iki koleksiyonları, kısıtlı bir Kartezyen ürün oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e8b07-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="e8b07-142">Önceki sorgu ifadesi her öğenin sağdaki nerede koleksiyonda her öğenin karşı eşleştirilmiş soldaki koleksiyonunun bileşimini işler `ON` koşul doğrudur.</span><span class="sxs-lookup"><span data-stu-id="e8b07-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="e8b07-143">Varsa `ON` koşul yanlış ise, ifade null değerine sahip sağdaki öğesi karşı eşleştirilmiş soldaki öğesinin bir örneği hala işler.</span><span class="sxs-lookup"><span data-stu-id="e8b07-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="e8b07-144">Ayrıca, soldaki null değerine sahip öğe karşı eşleştirilmiş sağdaki öğesinin bir örneğini işler.</span><span class="sxs-lookup"><span data-stu-id="e8b07-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8b07-145">İçinde SQL-92 ile uyumluluğu korumak için [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] dış anahtar sözcüğü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e8b07-145">To preserve compatibility with SQL-92, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] the OUTER keyword is optional.</span></span> <span data-ttu-id="e8b07-146">Bu nedenle, `LEFT JOIN`, `RIGHT JOIN`, ve `FULL JOIN` için eş anlamlı sözcükleri olan `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, ve `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="e8b07-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>  
  
### <a name="apply-clause-item"></a><span data-ttu-id="e8b07-147">Yan tümce öğesi UYGULA</span><span class="sxs-lookup"><span data-stu-id="e8b07-147">APPLY Clause Item</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e8b07-148"> iki tür destekler, `APPLY`: `CROSS APPLY` ve `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="e8b07-148"> supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>  
  
 <span data-ttu-id="e8b07-149">A `CROSS APPLY` her soldaki koleksiyon öğesi sağdaki ifadesinin hesaplanmasıyla oluşturulan koleksiyonun bir öğesi ile benzersiz eşleştirmesi üretir.</span><span class="sxs-lookup"><span data-stu-id="e8b07-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="e8b07-150">İle bir `CROSS APPLY`, sağdaki ifade aşağıdaki ilişkili koleksiyon örnekte gösterildiği gibi işlevsel olarak öğesi solda, bağlı:</span><span class="sxs-lookup"><span data-stu-id="e8b07-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 <span data-ttu-id="e8b07-151">Davranışını `CROSS APPLY` birleştirme listesine benzer.</span><span class="sxs-lookup"><span data-stu-id="e8b07-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="e8b07-152">Sağ ifade boş bir koleksiyon için değerlendirilirse `CROSS APPLY` soldaki öğesinin bu örneği için hiçbir değer çiftlerini üretir.</span><span class="sxs-lookup"><span data-stu-id="e8b07-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>  
  
 <span data-ttu-id="e8b07-153">Bir `OUTER APPLY` benzer bir `CROSS APPLY`, sağdaki ifade boş bir koleksiyon için bile değerlendirirken, bir eşleştirme hala üretilen dışında.</span><span class="sxs-lookup"><span data-stu-id="e8b07-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="e8b07-154">Aşağıdaki örneğidir bir `OUTER APPLY`:</span><span class="sxs-lookup"><span data-stu-id="e8b07-154">The following is an example of an `OUTER APPLY`:</span></span>  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  <span data-ttu-id="e8b07-155">Aksine, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], bir açık unnest adım için gerekli [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8b07-155">Unlike in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8b07-156">`CROSS` ve `OUTER APPLY` işleçleri sunuldu [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8b07-156">`CROSS` and `OUTER APPLY` operators were introduced in [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="e8b07-157">Bazı durumlarda, içeren Transact-SQL sorgusu ardışık düzen üretebilir `CROSS APPLY` ve/veya `OUTER APPLY` işleçler.</span><span class="sxs-lookup"><span data-stu-id="e8b07-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="e8b07-158">Çünkü SQL Server sürümleri dahil olmak üzere bazı arka uç sağlayıcıları öncesi [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], bu işleçlere desteklemez, bu tür sorgular bu arka uç sağlayıcılarının yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="e8b07-158">Because some backend providers, including versions of SQL Server earlier than [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
>   
>  <span data-ttu-id="e8b07-159">Varlığı için yol açabilecek bazı tipik senaryolar `CROSS APPLY` ve/veya `OUTER APPLY` çıkış sorgusunda işleçler şunlardır: sayfalama ile; ilişkili bir alt sorgu İlişkili bir alt sorgu veya gezinti tarafından üretilen bir koleksiyon üzerinden AnyElement; LINQ bir öğe Seçicisi kabul yöntemleri gruplandırma kullanan sorgular; bir sorguda bir `CROSS APPLY` veya bir `OUTER APPLY` açıkça belirtilir; olan bir sorgu bir `DEREF` üzerinden oluşturmak bir `REF` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e8b07-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>  
  
## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="e8b07-160">Birden çok koleksiyon FROM yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="e8b07-160">Multiple Collections in the FROM Clause</span></span>  
 <span data-ttu-id="e8b07-161">`FROM` Yan tümcesi virgülle ayırarak birden fazla koleksiyon içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e8b07-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="e8b07-162">Bu durumlarda, birlikte birleştirilecek koleksiyonları varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e8b07-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="e8b07-163">Bunlar çok yönlü çapraz birleştirme olarak düşünün.</span><span class="sxs-lookup"><span data-stu-id="e8b07-163">Think of these as an n-way CROSS JOIN.</span></span>  
  
 <span data-ttu-id="e8b07-164">Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlar, ancak `c.Names` bağlı `C`.</span><span class="sxs-lookup"><span data-stu-id="e8b07-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 <span data-ttu-id="e8b07-165">Önceki örnekte aşağıdaki örneğe mantıksal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="e8b07-165">The previous example is logically equivalent to the following example:</span></span>  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a><span data-ttu-id="e8b07-166">Sol bağıntı</span><span class="sxs-lookup"><span data-stu-id="e8b07-166">Left Correlation</span></span>  
 <span data-ttu-id="e8b07-167">Alanındaki öğelerin `FROM` yan tümcesi, önceki yan tümcelerinde belirtilen öğelere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="e8b07-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="e8b07-168">Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlar, ancak `c.Names` bağlı `C`:</span><span class="sxs-lookup"><span data-stu-id="e8b07-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 <span data-ttu-id="e8b07-169">Bu mantıksal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="e8b07-169">This is logically equivalent to:</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a><span data-ttu-id="e8b07-170">Semantiği</span><span class="sxs-lookup"><span data-stu-id="e8b07-170">Semantics</span></span>  
 <span data-ttu-id="e8b07-171">Mantıksal olarak koleksiyonlarda `FROM` yan tümcesi parçası olarak kabul bir `n`-yönlü çapraz birleştirme (1 yönlü söz konusu olduğunda çapraz birleştirme dışında).</span><span class="sxs-lookup"><span data-stu-id="e8b07-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="e8b07-172">Diğer adlar `FROM` yan tümcesi soldan sağa doğru işlem ve daha sonra başvurmak için geçerli bir kapsama eklenir.</span><span class="sxs-lookup"><span data-stu-id="e8b07-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="e8b07-173">`FROM` Yan tümcesi multiset satır üretmek için varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e8b07-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="e8b07-174">Her öğe için bir alan olacaktır `FROM` tek bir öğe bu koleksiyon öğeyi temsil eden yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e8b07-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>  
  
 <span data-ttu-id="e8b07-175">`FROM` Üretir mantıksal olarak multiset satır türü (c, d, e) satır yan tümcesi burada alanları c, d ve e öğesi türünü varsayılır `C`, `D`, ve `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="e8b07-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="e8b07-176"> Her basit için diğer ad tanıtır `FROM` kapsamında yan tümce öğesi.</span><span class="sxs-lookup"><span data-stu-id="e8b07-176"> introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="e8b07-177">Örneğin, aşağıdakileri yan tümcesi parçacığı gelen kapsam içine sunulan c, d ve e adlardır.</span><span class="sxs-lookup"><span data-stu-id="e8b07-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 <span data-ttu-id="e8b07-178">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (aksine [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` yan tümcesi yalnızca kapsam içine diğer adları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="e8b07-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="e8b07-179">Bu koleksiyonlardaki sütunlar (Özellikler) yönelik tüm başvuruları diğer ad ile nitelenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8b07-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>  
  
## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="e8b07-180">İç içe geçmiş sorgularından anahtarlarını çekme</span><span class="sxs-lookup"><span data-stu-id="e8b07-180">Pulling Up Keys from Nested Queries</span></span>  
 <span data-ttu-id="e8b07-181">Belirli türde bir iç içe bir sorgu anahtarları çekme gerektiren sorguları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e8b07-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="e8b07-182">Örneğin, aşağıdaki sorgusu geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="e8b07-182">For example, the following query is valid:</span></span>  
  
```  
select c.Orders from Customers as c   
```  
  
 <span data-ttu-id="e8b07-183">Ancak, iç içe sorgu herhangi bir anahtara sahip olmadığından aşağıdaki sorgusu geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="e8b07-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8b07-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8b07-184">See Also</span></span>  
 [<span data-ttu-id="e8b07-185">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e8b07-185">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e8b07-186">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="e8b07-186">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="e8b07-187">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="e8b07-187">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
