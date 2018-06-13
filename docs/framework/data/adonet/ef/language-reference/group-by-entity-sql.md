---
title: Grup (varlığıyla, SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 3b5edee08afef8418f19df433223818218ae909d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763192"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="aa654-102">Grup (varlığıyla, SQL)</span><span class="sxs-lookup"><span data-stu-id="aa654-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="aa654-103">Bir sorgu tarafından döndürülen hangi nesneleri içine grupları belirtir ([seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) ifade olan yerleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="aa654-103">Specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa654-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa654-104">Syntax</span></span>  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="aa654-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="aa654-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="aa654-106">Herhangi bir geçerli sorgu ifade gruplandırma gerçekleştirildiği.</span><span class="sxs-lookup"><span data-stu-id="aa654-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="aa654-107">`expression` bir özellik ya da FROM yan tümcesi tarafından döndürülen bir özelliğe başvuruyor toplama olmayan bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="aa654-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="aa654-108">Her bir GROUP BY yan tümcesi ifadesinde eşitlik için karşılaştırılabilir bir türe değerlendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa654-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="aa654-109">Bu sayı, dizeleri ve tarihleri gibi genellikle skaler temelleri türleridir.</span><span class="sxs-lookup"><span data-stu-id="aa654-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="aa654-110">Bir koleksiyona göre gruplandırma yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="aa654-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa654-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa654-111">Remarks</span></span>  
 <span data-ttu-id="aa654-112">SELECT yan tümcesinde toplama işlevleri eklenirse \<seçim listesi >, GROUP BY her grup için bir Özet değer hesaplar.</span><span class="sxs-lookup"><span data-stu-id="aa654-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="aa654-113">GROUP BY belirtildiğinde, her özellik adı seçim listesindeki herhangi bir zorunluluğu ifade GROUP BY listesinde eklenmesi veya GROUP BY ifadesi seçim listesi ifade tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="aa654-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa654-114">GROUP BY yan tümcesi tarafından döndürülen grupları ORDER BY yan tümcesi belirtilmezse, belirli bir sırada değildir.</span><span class="sxs-lookup"><span data-stu-id="aa654-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="aa654-115">Belirli bir verinin sıralamasını belirtmek için her zaman ORDER BY yan tümcesi kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="aa654-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="aa654-116">Örtük olarak (örneğin, sorgudaki HAVING yan tümcesi tarafından) veya bir GROUP BY yan tümcesi, ya da açıkça belirtildiğinde geçerli kapsamdaki gizlidir ve yeni bir kapsam sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="aa654-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="aa654-117">SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi artık FROM yan tümcesinde belirtilen öğe adları başvurmak mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="aa654-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="aa654-118">Yalnızca gruplandırma ifadeleri kendilerini başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="aa654-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="aa654-119">Bunu yapmak için her gruplandırma ifadesi yeni adları (diğer adlar) atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa654-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="aa654-120">Gruplandırma ifadesi için diğer ad belirtilmezse [!INCLUDE[esql](../../../../../../includes/esql-md.md)] aşağıdaki örnekte gösterildiği gibi diğer adı oluşturma kuralları kullanarak bir tane oluşturmak çalışır.</span><span class="sxs-lookup"><span data-stu-id="aa654-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="aa654-121">GROUP BY yan tümcesinde ifade önceki aynı GROUP BY yan tümcesinde tanımlanan adlarına başvuruda bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="aa654-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="aa654-122">Gruplandırma adları yanı sıra, SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi toplamalar de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa654-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="aa654-123">Bir toplama grubunun her öğe için değerlendirilen bir ifade içeriyor.</span><span class="sxs-lookup"><span data-stu-id="aa654-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="aa654-124">Toplama işleci tüm ifadelerin değerlerini azaltır (genellikle, ancak her zaman, tek bir değer içine).</span><span class="sxs-lookup"><span data-stu-id="aa654-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="aa654-125">Toplama ifadesi, özgün öğe adları görünür üst kapsamda veya GROUP BY yan tümcesi tarafından kendisine sunulan yeni adlarının herhangi biri için başvurular yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa654-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="aa654-126">Toplamalar SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi görünse de, bunlar aslında gruplandırma ifadeler aynı kapsamı altında aşağıdaki örnekte gösterildiği gibi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aa654-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="aa654-127">Bu sorgu, sipariş, tüm ürünleri maliyetini bir raporu oluşturmak için GROUP BY yan tümcesi kullanır. ürün göre ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="aa654-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="aa654-128">Ad verir `name` ürüne gruplandırma ifadesi ve ardından bu seçim listesinde ad başvuruları bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="aa654-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="aa654-129">Ayrıca bir toplama işlevinde belirtir `sum` seçim listesindeki fiyat ve miktar sipariş satırının dahili olarak başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="aa654-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="aa654-130">Her GROUP By anahtar ifadesi giriş kapsamına en az bir başvurusu olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="aa654-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="aa654-131">GROUP BY kullanma örneği için bkz: [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="aa654-131">For an example of using GROUP BY, see [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa654-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa654-132">Example</span></span>  
 <span data-ttu-id="aa654-133">Aşağıdaki varlık SQL sorgusunu GROUP BY işleci nesneleri bir sorgu tarafından döndürülen grupları belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa654-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="aa654-134">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="aa654-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="aa654-135">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="aa654-135">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="aa654-136">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="aa654-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="aa654-137">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="aa654-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="aa654-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa654-138">See Also</span></span>  
 [<span data-ttu-id="aa654-139">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa654-139">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="aa654-140">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="aa654-140">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
