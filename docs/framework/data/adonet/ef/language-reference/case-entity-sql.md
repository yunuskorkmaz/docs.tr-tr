---
description: 'Hakkında daha fazla bilgi edinin: CASE (Entity SQL)'
title: Büyük/küçük harf (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58f51aa46f41c3b502bcd6d364e893a12624f4cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739501"
---
# <a name="case-entity-sql"></a><span data-ttu-id="21a06-103">Büyük/küçük harf (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="21a06-103">CASE (Entity SQL)</span></span>

<span data-ttu-id="21a06-104">`Boolean`Sonucu belirleyecek bir ifade kümesi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="21a06-104">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21a06-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="21a06-105">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="21a06-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="21a06-106">Arguments</span></span>  

 `n`  
 <span data-ttu-id="21a06-107">, `Boolean_expression` Yan tümcelerinin kullanılabileceğini gösteren bir yer tutucudur `result_expression` .</span><span class="sxs-lookup"><span data-stu-id="21a06-107">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="21a06-108">NI `result_expression`</span><span class="sxs-lookup"><span data-stu-id="21a06-108">THEN `result_expression`</span></span>  
 <span data-ttu-id="21a06-109">, Olarak değerlendirildiğinde döndürülen ifadedir `Boolean_expression` `true` .</span><span class="sxs-lookup"><span data-stu-id="21a06-109">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="21a06-110">`result expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="21a06-110">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="21a06-111">DEĞILSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="21a06-111">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="21a06-112">, Hiçbir karşılaştırma işleminin değerlendirilmediğinde döndürülen ifadedir `true` .</span><span class="sxs-lookup"><span data-stu-id="21a06-112">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="21a06-113">Bu bağımsız değişken atlanırsa ve bir karşılaştırma işlemi olarak değerlendiriliyorsa `true` , Case null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="21a06-113">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="21a06-114">`else_result_expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="21a06-114">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="21a06-115">Ve ' nin veri türleri `else_result_expression` `result_expression` aynı olmalıdır veya örtük bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21a06-115">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="21a06-116">OLUŞTURULURKEN `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="21a06-116">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="21a06-117">, `Boolean` Aranan Case biçimi kullanıldığında değerlendirilen ifadedir.</span><span class="sxs-lookup"><span data-stu-id="21a06-117">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="21a06-118">`Boolean_expression` geçerli bir `Boolean` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="21a06-118">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21a06-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21a06-119">Return Value</span></span>  

 <span data-ttu-id="21a06-120">İçindeki tür kümesinden en yüksek öncelik türünü, `result_expression` ve isteğe bağlı olarak döndürür `else_result_expression` .</span><span class="sxs-lookup"><span data-stu-id="21a06-120">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21a06-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21a06-121">Remarks</span></span>  

 <span data-ttu-id="21a06-122">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Case Ifadesi Transact-SQL Case ifadesine benzer.</span><span class="sxs-lookup"><span data-stu-id="21a06-122">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="21a06-123">Hangi ifadenin uygun sonucu olacağını belirleyen bir dizi koşullu test oluşturmak için Case ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="21a06-123">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="21a06-124">Case ifadesinin bu biçimi, `Boolean` doğru sonuç ifadesini belirlemekte bir veya daha fazla ifadeye yönelik bir dizi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="21a06-124">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="21a06-125">CASE işlevi, `Boolean_expression` belirtilen sırada her bir yan tümce için değerlendirilir ve öğesini `result_expression` değerlendiren ilk döndürür `Boolean_expression` `true` .</span><span class="sxs-lookup"><span data-stu-id="21a06-125">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="21a06-126">Kalan ifadeler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="21a06-126">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="21a06-127">Hiçbir `Boolean_expression` değerlendirme yoksa `true` , veritabanı altyapısı `else_result_expression` Eğer bir else yan TÜMCESI belirtilmişse veya else yan tümcesi belirtilmemişse null değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="21a06-127">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="21a06-128">CASE deyimleri bir çoklu küme döndüremez.</span><span class="sxs-lookup"><span data-stu-id="21a06-128">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21a06-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="21a06-129">Example</span></span>  

 <span data-ttu-id="21a06-130">Aşağıdaki Entity SQL sorgusu, `Boolean` sonucu tespit etmek için bir dizi ifadeyi değerlendirmek üzere Case ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="21a06-130">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="21a06-131">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="21a06-131">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="21a06-132">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="21a06-132">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="21a06-133">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="21a06-133">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="21a06-134">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="21a06-134">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="21a06-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21a06-135">See also</span></span>

- [<span data-ttu-id="21a06-136">NI</span><span class="sxs-lookup"><span data-stu-id="21a06-136">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="21a06-137">SELECT</span><span class="sxs-lookup"><span data-stu-id="21a06-137">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="21a06-138">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="21a06-138">Entity SQL Reference</span></span>](entity-sql-reference.md)
