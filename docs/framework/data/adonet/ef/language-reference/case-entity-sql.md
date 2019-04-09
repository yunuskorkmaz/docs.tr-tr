---
title: Durum (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 65d038564683e0a97939cabc7081be3341f4542d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162808"
---
# <a name="case-entity-sql"></a><span data-ttu-id="7e8b1-102">Durum (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="7e8b1-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="7e8b1-103">Bir dizi olarak değerlendirilir `Boolean` sonucu belirlemek için ifadeler.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e8b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e8b1-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="7e8b1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7e8b1-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="7e8b1-106">Bu çoklu gösteren bir yer tutucudur, `Boolean_expression` ARDINDAN `result_expression` yan tümceleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="7e8b1-107">THEN</span><span class="sxs-lookup"><span data-stu-id="7e8b1-107">THEN</span></span> `result_expression`  
 <span data-ttu-id="7e8b1-108">İfade olduğunda döndürülen `Boolean_expression` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> `result expression` <span data-ttu-id="7e8b1-109">Herhangi bir geçerli ifade var.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-109">is any valid expression.</span></span>  
  
 <span data-ttu-id="7e8b1-110">ELSE</span><span class="sxs-lookup"><span data-stu-id="7e8b1-110">ELSE</span></span> `else_result_expression`  
 <span data-ttu-id="7e8b1-111">İfade yok karşılaştırma işlemi olmaması halinde döndürülür `true`.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="7e8b1-112">Bu bağımsız değişken atlanırsa ve herhangi bir karşılaştırma işleminin sonucunu veren `true`, servis talebi null döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> `else_result_expression` <span data-ttu-id="7e8b1-113">Herhangi bir geçerli ifade var.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-113">is any valid expression.</span></span> <span data-ttu-id="7e8b1-114">Veri türlerini `else_result_expression` ve tüm `result_expression` örtük bir dönüştürme olmalıdır veya aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="7e8b1-115">NE ZAMAN</span><span class="sxs-lookup"><span data-stu-id="7e8b1-115">WHEN</span></span> `Boolean_expression`  
 <span data-ttu-id="7e8b1-116">Olan `Boolean` Aranan büyük/küçük harf biçimi kullanıldığında değerlendirilen ifade.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> `Boolean_expression` <span data-ttu-id="7e8b1-117">herhangi bir geçerli olduğu `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-117">is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e8b1-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7e8b1-118">Return Value</span></span>  
 <span data-ttu-id="7e8b1-119">Kümesinden türlerinde en yüksek öncelik türünü döndürüyor `result_expression` ve isteğe bağlı `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e8b1-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e8b1-120">Remarks</span></span>  
 <span data-ttu-id="7e8b1-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Case ifadesi benzer [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case ifadesi.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case expression.</span></span> <span data-ttu-id="7e8b1-122">Case ifadesi, bir dizi hangi ifadesi uygun bir sonuç verir belirlemek için koşullu test yapmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="7e8b1-123">Case ifadesi bu tür bir dizi bir veya daha fazla geçerli `Boolean` doğru sonuç ifadesi belirlemek için ifadeler.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="7e8b1-124">Durum işlevi değerlendirir `Boolean_expression` her zaman yan tümcesi sırada belirtilen ve döndürür `result_expression` ilk `Boolean_expression` olarak değerlendirilen `true`.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="7e8b1-125">Kalan ifade değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="7e8b1-126">Hayır ise `Boolean_expression` değerlendiren `true`, veritabanı altyapısı döndürür `else_result_expression` ELSE yan belirtilmezse, ya da ELSE yan tümce belirtilirse bir null değer.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="7e8b1-127">CASE ifadesi, bir çoklu küme döndüremez.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e8b1-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e8b1-128">Example</span></span>  
 <span data-ttu-id="7e8b1-129">Aşağıdaki varlık SQL sorgusu, bir dizi değerlendirmek için CASE ifadesi kullanır. `Boolean` sonucu belirlemek üzere ifadeler.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="7e8b1-130">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7e8b1-131">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="7e8b1-131">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7e8b1-132">Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7e8b1-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="7e8b1-133">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7e8b1-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="7e8b1-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e8b1-134">See also</span></span>

- [<span data-ttu-id="7e8b1-135">THEN</span><span class="sxs-lookup"><span data-stu-id="7e8b1-135">THEN</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)
- [<span data-ttu-id="7e8b1-136">SEÇ</span><span class="sxs-lookup"><span data-stu-id="7e8b1-136">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [<span data-ttu-id="7e8b1-137">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7e8b1-137">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
