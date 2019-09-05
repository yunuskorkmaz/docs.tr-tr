---
title: Büyük/küçük harf (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 79544f4180313a008669c56c4f2740c889043c6d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251248"
---
# <a name="case-entity-sql"></a><span data-ttu-id="dccf8-102">Büyük/küçük harf (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dccf8-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="dccf8-103">Sonucu belirleyecek bir `Boolean` ifade kümesi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="dccf8-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dccf8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dccf8-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="dccf8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dccf8-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="dccf8-106">, Yan `Boolean_expression` tümcelerinin `result_expression` kullanılabileceğini gösteren bir yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="dccf8-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="dccf8-107">NI`result_expression`</span><span class="sxs-lookup"><span data-stu-id="dccf8-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="dccf8-108">, Olarak `Boolean_expression` `true`değerlendirildiğinde döndürülen ifadedir.</span><span class="sxs-lookup"><span data-stu-id="dccf8-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="dccf8-109">`result expression`geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="dccf8-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="dccf8-110">DEĞILSE`else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="dccf8-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="dccf8-111">, Hiçbir karşılaştırma işleminin değerlendirilmediğinde `true`döndürülen ifadedir.</span><span class="sxs-lookup"><span data-stu-id="dccf8-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="dccf8-112">Bu bağımsız değişken atlanırsa ve bir karşılaştırma işlemi olarak `true`değerlendiriliyorsa, Case null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="dccf8-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="dccf8-113">`else_result_expression`geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="dccf8-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="dccf8-114">Ve ' `else_result_expression`ninveritürleri aynıolmalıdırveyaörtükbirdönüştürmeolmalıdır.`result_expression`</span><span class="sxs-lookup"><span data-stu-id="dccf8-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="dccf8-115">OLUŞTURULURKEN`Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="dccf8-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="dccf8-116">, Aranan Case biçimi kullanıldığında değerlendirilen ifadedir.`Boolean`</span><span class="sxs-lookup"><span data-stu-id="dccf8-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="dccf8-117">`Boolean_expression`geçerli `Boolean` bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="dccf8-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dccf8-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dccf8-118">Return Value</span></span>  
 <span data-ttu-id="dccf8-119">İçindeki tür kümesinden en yüksek öncelik türünü, `result_expression` ve isteğe bağlı `else_result_expression`olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="dccf8-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dccf8-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dccf8-120">Remarks</span></span>  
 <span data-ttu-id="dccf8-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Case ifadesi Transact-SQL Case ifadesine benzer.</span><span class="sxs-lookup"><span data-stu-id="dccf8-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="dccf8-122">Hangi ifadenin uygun sonucu olacağını belirleyen bir dizi koşullu test oluşturmak için Case ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dccf8-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="dccf8-123">Case ifadesinin bu biçimi, doğru sonuç ifadesini belirlemekte bir veya daha fazla `Boolean` ifadeye yönelik bir dizi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dccf8-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="dccf8-124">Case işlevi, belirtilen `Boolean_expression` sırada her bir yan tümce için değerlendirilir ve öğesini değerlendiren `true`ilk `result_expression` `Boolean_expression` döndürür.</span><span class="sxs-lookup"><span data-stu-id="dccf8-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="dccf8-125">Kalan ifadeler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="dccf8-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="dccf8-126">Hiçbir `Boolean_expression` `else_result_expression` değerlendirme yoksa, veritabanı altyapısı Eğer bir else yan tümcesi belirtilmişse veya else yan tümcesi belirtilmemişse null değeri döndürür. `true`</span><span class="sxs-lookup"><span data-stu-id="dccf8-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="dccf8-127">CASE deyimleri bir çoklu küme döndüremez.</span><span class="sxs-lookup"><span data-stu-id="dccf8-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dccf8-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="dccf8-128">Example</span></span>  
 <span data-ttu-id="dccf8-129">Aşağıdaki Entity SQL sorgusu, sonucu tespit etmek için bir dizi `Boolean` ifadeyi değerlendirmek üzere Case ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dccf8-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="dccf8-130">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="dccf8-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dccf8-131">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="dccf8-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="dccf8-132">[Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="dccf8-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="dccf8-133">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="dccf8-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="dccf8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dccf8-134">See also</span></span>

- [<span data-ttu-id="dccf8-135">THEN</span><span class="sxs-lookup"><span data-stu-id="dccf8-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="dccf8-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="dccf8-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="dccf8-137">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="dccf8-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
