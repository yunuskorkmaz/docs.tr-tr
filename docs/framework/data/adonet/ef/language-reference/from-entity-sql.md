---
title: (Varlıktan, SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 3cc02b4c51b32d0faace4d89d0c6c1f6923dd138
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119840"
---
# <a name="from-entity-sql"></a><span data-ttu-id="0b46e-102">(Varlıktan, SQL)</span><span class="sxs-lookup"><span data-stu-id="0b46e-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="0b46e-103">Kullanılan koleksiyon belirtir [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="0b46e-103">Specifies the collection used in [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b46e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b46e-104">Syntax</span></span>  
  
```  
FROM expression [ ,...n ] as C  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b46e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0b46e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0b46e-106">Bir kaynağı olarak kullanılacak bir koleksiyon verir herhangi bir geçerli sorgu ifade bir `SELECT` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0b46e-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b46e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b46e-107">Remarks</span></span>  
 <span data-ttu-id="0b46e-108">A `FROM` yan tümcesi, bir veya daha fazla virgülle ayrılmış listesi `FROM` yan tümcesi öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0b46e-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="0b46e-109">`FROM` Yan tümcesi için bir veya daha fazla kaynakları belirtmek için kullanılabilir bir `SELECT` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0b46e-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="0b46e-110">En basit biçimi bir `FROM` yan tümcesi olan bir koleksiyon ve kaynak olarak kullanılan bir diğer ad tanımlayan tek bir sorgu ifadesinin bir `SELECT` aşağıdaki örnekte gösterildiği gibi deyimi:</span><span class="sxs-lookup"><span data-stu-id="0b46e-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>  
  
 `FROM C as c`  
  
## <a name="from-clause-items"></a><span data-ttu-id="0b46e-111">Yan tümcesi öğeleri</span><span class="sxs-lookup"><span data-stu-id="0b46e-111">FROM Clause Items</span></span>  
 <span data-ttu-id="0b46e-112">Her `FROM` yan tümce öğesi bir kaynak koleksiyonu başvurduğu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="0b46e-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0b46e-113">Aşağıdaki sınıfları destekler `FROM` yan öğeler: basit `FROM` yan tümcesi öğeleri `JOIN FROM` yan tümcesi öğeleri ve `APPLY FROM` yan tümcesi öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0b46e-113">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="0b46e-114">Bunların her biri `FROM` yan öğeler aşağıdaki bölümlerde daha ayrıntılı açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b46e-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>  
  
### <a name="simple-from-clause-item"></a><span data-ttu-id="0b46e-115">Basit yan tümce öğesi</span><span class="sxs-lookup"><span data-stu-id="0b46e-115">Simple FROM Clause Item</span></span>  
 <span data-ttu-id="0b46e-116">En basit `FROM` yan tümce öğesi olan bir koleksiyon ve bir diğer ad tanımlayan tek bir ifade.</span><span class="sxs-lookup"><span data-stu-id="0b46e-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="0b46e-117">İfade, yalnızca bir varlık kümesini veya alt sorgu veya koleksiyon türü herhangi bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="0b46e-118">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0b46e-118">The following is an example:</span></span>  
  
```  
LOB.Customers as c  
```  
  
 <span data-ttu-id="0b46e-119">Diğer ad belirtimi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b46e-119">The alias specification is optional.</span></span> <span data-ttu-id="0b46e-120">Yan tümce öğesi Yukarıdakilerden alternatif bir belirtimi şu olabilir:</span><span class="sxs-lookup"><span data-stu-id="0b46e-120">An alternate specification of the above from clause item could be the following:</span></span>  
  
```  
LOB.Customers  
```  
  
 <span data-ttu-id="0b46e-121">Diğer ad yok belirtilirse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] koleksiyon ifadeye göre bir diğer ad oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="0b46e-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>  
  
### <a name="join-from-clause-item"></a><span data-ttu-id="0b46e-122">FROM yan tümce öğesi katılın</span><span class="sxs-lookup"><span data-stu-id="0b46e-122">JOIN FROM Clause Item</span></span>  
 <span data-ttu-id="0b46e-123">A `JOIN FROM` yan tümce öğesi temsil eder, ikisi arasında bir birleştirme `FROM` yan tümcesi öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0b46e-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0b46e-124">destekler, birleşimler, İç birleşimler sol ve sağ dış birleşimler ve tam dış birleştirmeler arası.</span><span class="sxs-lookup"><span data-stu-id="0b46e-124">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="0b46e-125">Bu birleştirme benzer şekilde, desteklenen desteklenen [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b46e-125">All these joins are supported similar to the way that they are supported in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0b46e-126">Olarak [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], iki `FROM` söz konusu yan tümcesi öğeleri `JOIN` bağımsız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b46e-126">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="0b46e-127">Diğer bir deyişle, bunlar büyük olamaz.</span><span class="sxs-lookup"><span data-stu-id="0b46e-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="0b46e-128">A `CROSS APPLY` veya `OUTER APPLY` bu durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>  
  
#### <a name="cross-joins"></a><span data-ttu-id="0b46e-129">Çapraz birleştirme</span><span class="sxs-lookup"><span data-stu-id="0b46e-129">Cross Joins</span></span>  
 <span data-ttu-id="0b46e-130">A `CROSS JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyon Kartezyen ürün oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0b46e-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c CROSS JOIN D as d`  
  
#### <a name="inner-joins"></a><span data-ttu-id="0b46e-131">İç birleşimler</span><span class="sxs-lookup"><span data-stu-id="0b46e-131">Inner Joins</span></span>  
 <span data-ttu-id="0b46e-132">Bir `INNER JOIN` aşağıdaki örnekte gösterildiği gibi iki koleksiyon kısıtlanmış bir Kartezyen ürün oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0b46e-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c [INNER] JOIN D AS d ON e`  
  
 <span data-ttu-id="0b46e-133">Önceki sorgu ifadesinin sağ nerede hakkında koleksiyonun her öğesine karşı eşleştirilmiş sol taraftaki koleksiyonun her öğesine bir birleşimini işler `ON` koşul true ise.</span><span class="sxs-lookup"><span data-stu-id="0b46e-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="0b46e-134">Hayır ise `ON` koşul belirtilirse, bir `INNER JOIN` için degenerates bir `CROSS JOIN`.</span><span class="sxs-lookup"><span data-stu-id="0b46e-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>  
  
#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="0b46e-135">Sol dış birleştirmeler ve sağ dış birleşimler</span><span class="sxs-lookup"><span data-stu-id="0b46e-135">Left Outer Joins and Right Outer Joins</span></span>  
 <span data-ttu-id="0b46e-136">Bir `OUTER JOIN` sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyon kısıtlanmış bir Kartezyen ürün oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0b46e-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>  
  
 `FROM C AS c LEFT OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="0b46e-137">Önceki sorgu ifadesinin sağ nerede hakkında koleksiyonun her öğesine karşı eşleştirilmiş sol taraftaki koleksiyonun her öğesine bir birleşimini işler `ON` koşul true ise.</span><span class="sxs-lookup"><span data-stu-id="0b46e-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="0b46e-138">Varsa `ON` koşul false ise, ifade hala öğesi null değerine sahip sağdaki karşı eşleştirilmiş soldaki öğeyi tek bir örneğini işler.</span><span class="sxs-lookup"><span data-stu-id="0b46e-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>  
  
 <span data-ttu-id="0b46e-139">A `RIGHT OUTER JOIN` benzer bir şekilde ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>  
  
#### <a name="full-outer-joins"></a><span data-ttu-id="0b46e-140">Tam dış birleşimler</span><span class="sxs-lookup"><span data-stu-id="0b46e-140">Full Outer Joins</span></span>  
 <span data-ttu-id="0b46e-141">Açık bir `FULL OUTER JOIN` aşağıdaki örnekte gösterildiği gibi iki koleksiyon kısıtlanmış bir Kartezyen ürün oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0b46e-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>  
  
 `FROM C AS c FULL OUTER JOIN D AS d ON e`  
  
 <span data-ttu-id="0b46e-142">Önceki sorgu ifadesinin sağ nerede hakkında koleksiyonun her öğesine karşı eşleştirilmiş sol taraftaki koleksiyonun her öğesine bir birleşimini işler `ON` koşul true ise.</span><span class="sxs-lookup"><span data-stu-id="0b46e-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="0b46e-143">Varsa `ON` koşul false ise, ifade hala öğesi null değerine sahip sağdaki karşı eşleştirilmiş soldaki öğesinin bir örneğini işler.</span><span class="sxs-lookup"><span data-stu-id="0b46e-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="0b46e-144">Ayrıca, öğe null değeri ile sol taraftaki karşı eşleştirilmiş sağdaki öğesinin bir örneğini işler.</span><span class="sxs-lookup"><span data-stu-id="0b46e-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b46e-145">İçinde SQL 92, uyumluluğu korumak için [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] dış anahtar sözcüğü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b46e-145">To preserve compatibility with SQL-92, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] the OUTER keyword is optional.</span></span> <span data-ttu-id="0b46e-146">Bu nedenle, `LEFT JOIN`, `RIGHT JOIN`, ve `FULL JOIN` için eş anlamlı sözcükler olan `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, ve `FULL OUTER JOIN`.</span><span class="sxs-lookup"><span data-stu-id="0b46e-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>  
  
### <a name="apply-clause-item"></a><span data-ttu-id="0b46e-147">Geçerli yan tümce öğesi</span><span class="sxs-lookup"><span data-stu-id="0b46e-147">APPLY Clause Item</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0b46e-148">iki tür destekler, `APPLY`: `CROSS APPLY` ve `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="0b46e-148">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>  
  
 <span data-ttu-id="0b46e-149">A `CROSS APPLY` sol taraftaki koleksiyonun her öğesine sağ ifade tarafından değerlendirilen koleksiyonun bir öğesi ile benzersiz eşleştirmesi üretir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="0b46e-150">İle bir `CROSS APPLY`, sağdaki ifade ilişkili koleksiyon aşağıdaki örnekte gösterildiği gibi işlevsel olarak öğe sol taraftaki bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="0b46e-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>  
  
 `SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`  
  
 <span data-ttu-id="0b46e-151">Davranışını `CROSS APPLY` birleştirme listeye benzer.</span><span class="sxs-lookup"><span data-stu-id="0b46e-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="0b46e-152">Sağ ifade boş bir koleksiyon olarak değerlendirilirse `CROSS APPLY` öğenin sol taraftaki Bu örnek için hiçbir değer çiftlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0b46e-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>  
  
 <span data-ttu-id="0b46e-153">Bir `OUTER APPLY` benzer bir `CROSS APPLY`bile boş bir koleksiyon için sağ taraftaki ifade sonucunu verdiğinde bir eşleştirme hala üretilen dışında.</span><span class="sxs-lookup"><span data-stu-id="0b46e-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="0b46e-154">Aşağıdaki örneğidir bir `OUTER APPLY`:</span><span class="sxs-lookup"><span data-stu-id="0b46e-154">The following is an example of an `OUTER APPLY`:</span></span>  
  
 `SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`  
  
> [!NOTE]
>  <span data-ttu-id="0b46e-155">Aksine, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], gerekli olmadığı için bir açık unnest adımda [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b46e-155">Unlike in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
> [!NOTE]
>  `CROSS` <span data-ttu-id="0b46e-156">ve `OUTER APPLY` işleçleri de kullanıma sunulmuştur [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b46e-156">and `OUTER APPLY` operators were introduced in [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="0b46e-157">Bazı durumlarda, sorgu işlem hattındaki içeren Transact-SQL üretebilir `CROSS APPLY` ve/veya `OUTER APPLY` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="0b46e-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="0b46e-158">İçin SQL Server sürümleri dahil olmak üzere bazı arka uç sağlayıcıları öncesi [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], bu işleçleri desteklemez, bu arka uç sağlayıcılarında sorgularını yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="0b46e-158">Because some backend providers, including versions of SQL Server earlier than [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)], do not support these operators, such queries cannot be executed on these backend providers.</span></span>  
>   
>  <span data-ttu-id="0b46e-159">Varlığı için yol açabilecek bazı genel senaryolara `CROSS APPLY` ve/veya `OUTER APPLY` çıkış sorgu işleçler şunlardır: disk belleği ile; ilişkili alt sorgu AnyElement bağıntılı alt sorgu veya gezinti tarafından üretilen bir koleksiyon üzerinden; LINQ öğe Seçici kabul yöntemleri gruplandırma kullanan sorgular; bir sorguda bir `CROSS APPLY` veya `OUTER APPLY` açıkça belirtilir; olan bir sorgu bir `DEREF` üzerinden oluşturmak bir `REF` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b46e-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>  
  
## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="0b46e-160">Birden çok koleksiyon FROM yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="0b46e-160">Multiple Collections in the FROM Clause</span></span>  
 <span data-ttu-id="0b46e-161">`FROM` Yan tümcesi, virgülle ayırarak birden fazla koleksiyon bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="0b46e-162">Bu durumlarda, koleksiyonları birlikte katılması kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="0b46e-163">Bu çok yönlü çapraz birleştirme olarak düşünün.</span><span class="sxs-lookup"><span data-stu-id="0b46e-163">Think of these as an n-way CROSS JOIN.</span></span>  
  
 <span data-ttu-id="0b46e-164">Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlar, ancak `c.Names` bağlıdır `C`.</span><span class="sxs-lookup"><span data-stu-id="0b46e-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>  
  
```  
FROM C AS c, D AS d, c.Names AS e  
```  
  
 <span data-ttu-id="0b46e-165">Önceki örnekte, mantıksal olarak aşağıdaki örneğe eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="0b46e-165">The previous example is logically equivalent to the following example:</span></span>  
  
 `FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`  
  
## <a name="left-correlation"></a><span data-ttu-id="0b46e-166">Sol bağıntı</span><span class="sxs-lookup"><span data-stu-id="0b46e-166">Left Correlation</span></span>  
 <span data-ttu-id="0b46e-167">Öğeler `FROM` yan tümcesi, önceki yan tümcelerinde belirtilen öğelere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="0b46e-168">Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlar, ancak `c.Names` bağlıdır `C`:</span><span class="sxs-lookup"><span data-stu-id="0b46e-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>  
  
```  
from C as c, D as d, c.Names as e  
```  
  
 <span data-ttu-id="0b46e-169">Bu mantıksal olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-169">This is logically equivalent to:</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
## <a name="semantics"></a><span data-ttu-id="0b46e-170">Semantiği</span><span class="sxs-lookup"><span data-stu-id="0b46e-170">Semantics</span></span>  
 <span data-ttu-id="0b46e-171">Mantıksal olarak koleksiyonlarında `FROM` yan tümcesi olduğu varsayılır parçası olarak bir `n`-(1-şekilde söz konusu olduğunda çapraz birleştirme dışında) şekilde çapraz birleştirme.</span><span class="sxs-lookup"><span data-stu-id="0b46e-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="0b46e-172">Diğer adlar `FROM` yan tümcesi, soldan sağa doğru işlem ve daha sonra başvurmak için geçerli bir kapsama eklenir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="0b46e-173">`FROM` Yan tümcesi, bir çoklu küme satır üretmek için varsayılır.</span><span class="sxs-lookup"><span data-stu-id="0b46e-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="0b46e-174">Her öğe için bir alan olacaktır `FROM` yan tümcesi bu koleksiyon öğesi tek bir öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b46e-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>  
  
 <span data-ttu-id="0b46e-175">`FROM` Üretir mantıksal olarak bir çoklu küme türü (c, d, e) satır satır yan tümcesi burada alanları c, d ve e öğe türünde oldukları varsayılır `C`, `D`, ve `c.Names`.</span><span class="sxs-lookup"><span data-stu-id="0b46e-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="0b46e-176">Her basit için bir diğer ad tanıtır `FROM` kapsamda yan tümce öğesi.</span><span class="sxs-lookup"><span data-stu-id="0b46e-176">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="0b46e-177">Örneğin, aşağıdakilerden yan tümcesi kod parçacığı, kapsam içinde tanıtılan c, d ve e adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="0b46e-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>  
  
```  
from (C as c join D as d) cross apply c.Names as e  
```  
  
 <span data-ttu-id="0b46e-178">İçinde [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (aksine [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), `FROM` yan tümce kapsamına yalnızca diğer adları ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="0b46e-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="0b46e-179">Bu koleksiyonun sütunları (özellikleri) tüm başvuruları diğer adıyla nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0b46e-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>  
  
## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="0b46e-180">İç içe geçmiş sorgularından anahtarlarını çekiliyor</span><span class="sxs-lookup"><span data-stu-id="0b46e-180">Pulling Up Keys from Nested Queries</span></span>  
 <span data-ttu-id="0b46e-181">Belirli türlerdeki anahtarlarını iç içe geçmiş bir sorgunun çekmek gerektiren sorguları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0b46e-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="0b46e-182">Örneğin, aşağıdaki sorgusu geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="0b46e-182">For example, the following query is valid:</span></span>  
  
```  
select c.Orders from Customers as c   
```  
  
 <span data-ttu-id="0b46e-183">Ancak, iç içe sorgu herhangi bir anahtar olmadığından aşağıdaki sorgu geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="0b46e-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>  
  
```  
select {1} from {2, 3}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b46e-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b46e-184">See also</span></span>

- [<span data-ttu-id="0b46e-185">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0b46e-185">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="0b46e-186">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="0b46e-186">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [<span data-ttu-id="0b46e-187">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="0b46e-187">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
