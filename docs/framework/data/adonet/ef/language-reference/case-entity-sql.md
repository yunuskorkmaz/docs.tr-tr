---
title: Büyük/küçük harf (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 7c1e02d44c674bf262f92df1c43bec6e9f2143c5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039935"
---
# <a name="case-entity-sql"></a><span data-ttu-id="a8833-102">Büyük/küçük harf (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a8833-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="a8833-103">Sonucu belirleyecek bir `Boolean` ifadeleri kümesi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="a8833-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8833-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8833-104">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="a8833-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a8833-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="a8833-106">`Boolean_expression`, `result_expression` yan tümcelerinin kullanılabileceğini gösteren bir yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="a8833-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="a8833-107">SONRA `result_expression`</span><span class="sxs-lookup"><span data-stu-id="a8833-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="a8833-108">, `Boolean_expression` `true`değerlendirildiğinde döndürülen ifadedir.</span><span class="sxs-lookup"><span data-stu-id="a8833-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="a8833-109">`result expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="a8833-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="a8833-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="a8833-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="a8833-111">Bir karşılaştırma işlemi `true`olarak değerlendirilmediğinde ifade döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a8833-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="a8833-112">Bu bağımsız değişken atlanırsa ve hiçbir karşılaştırma işlemi `true`olarak değerlendirilirse, CASE null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a8833-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="a8833-113">`else_result_expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="a8833-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="a8833-114">`else_result_expression` veri türleri ve herhangi bir `result_expression` aynı olmalıdır veya örtük bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8833-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="a8833-115">`Boolean_expression` olduğunda</span><span class="sxs-lookup"><span data-stu-id="a8833-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="a8833-116">, Aranan CASE biçimi kullanıldığında `Boolean` ifade değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a8833-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="a8833-117">`Boolean_expression` geçerli `Boolean` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="a8833-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8833-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a8833-118">Return Value</span></span>  
 <span data-ttu-id="a8833-119">`result_expression` ve isteğe bağlı `else_result_expression`tür kümesinden en yüksek öncelik türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="a8833-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8833-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8833-120">Remarks</span></span>  
 <span data-ttu-id="a8833-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] case ifadesi Transact-SQL Case ifadesine benzer.</span><span class="sxs-lookup"><span data-stu-id="a8833-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="a8833-122">Hangi ifadenin uygun sonucu olacağını belirleyen bir dizi koşullu test oluşturmak için Case ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8833-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="a8833-123">Case ifadesinin bu biçimi, doğru sonuç ifadesini belirlemekte bir veya daha fazla `Boolean` ifadesi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a8833-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="a8833-124">CASE işlevi, belirtilen sırada her bir for yan tümcesi için `Boolean_expression` değerlendirir ve `true`değerlendirilen ilk `Boolean_expression` `result_expression` döndürür.</span><span class="sxs-lookup"><span data-stu-id="a8833-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="a8833-125">Kalan ifadeler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="a8833-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="a8833-126">Hiçbir `Boolean_expression` `true`değerlendiriyorsa, veritabanı altyapısı bir ELSE yan tümcesi belirtilmişse `else_result_expression` döndürür ya da ELSE yan tümcesi belirtilmemişse null bir değer olur.</span><span class="sxs-lookup"><span data-stu-id="a8833-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="a8833-127">CASE deyimleri bir çoklu küme döndüremez.</span><span class="sxs-lookup"><span data-stu-id="a8833-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8833-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8833-128">Example</span></span>  
 <span data-ttu-id="a8833-129">Aşağıdaki Entity SQL sorgusu, sonucu tespit etmek için bir dizi `Boolean` ifadeyi değerlendirmek üzere CASE ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8833-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="a8833-130">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="a8833-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a8833-131">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a8833-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a8833-132">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="a8833-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="a8833-133">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="a8833-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="a8833-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8833-134">See also</span></span>

- [<span data-ttu-id="a8833-135">THEN</span><span class="sxs-lookup"><span data-stu-id="a8833-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="a8833-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="a8833-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="a8833-137">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a8833-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
