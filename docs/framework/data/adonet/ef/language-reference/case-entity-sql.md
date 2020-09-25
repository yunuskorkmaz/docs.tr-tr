---
title: Büyük/küçük harf (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 65efedd36401db402a32748afaebff0f2af9f2a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185229"
---
# <a name="case-entity-sql"></a><span data-ttu-id="2cf0c-102">Büyük/küçük harf (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2cf0c-102">CASE (Entity SQL)</span></span>

<span data-ttu-id="2cf0c-103">`Boolean`Sonucu belirleyecek bir ifade kümesi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf0c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2cf0c-104">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="2cf0c-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2cf0c-105">Arguments</span></span>  

 `n`  
 <span data-ttu-id="2cf0c-106">, `Boolean_expression` Yan tümcelerinin kullanılabileceğini gösteren bir yer tutucudur `result_expression` .</span><span class="sxs-lookup"><span data-stu-id="2cf0c-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="2cf0c-107">NI `result_expression`</span><span class="sxs-lookup"><span data-stu-id="2cf0c-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="2cf0c-108">, Olarak değerlendirildiğinde döndürülen ifadedir `Boolean_expression` `true` .</span><span class="sxs-lookup"><span data-stu-id="2cf0c-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="2cf0c-109">`result expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="2cf0c-110">DEĞILSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="2cf0c-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="2cf0c-111">, Hiçbir karşılaştırma işleminin değerlendirilmediğinde döndürülen ifadedir `true` .</span><span class="sxs-lookup"><span data-stu-id="2cf0c-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="2cf0c-112">Bu bağımsız değişken atlanırsa ve bir karşılaştırma işlemi olarak değerlendiriliyorsa `true` , Case null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="2cf0c-113">`else_result_expression` geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="2cf0c-114">Ve ' nin veri türleri `else_result_expression` `result_expression` aynı olmalıdır veya örtük bir dönüştürme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="2cf0c-115">OLUŞTURULURKEN `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="2cf0c-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="2cf0c-116">, `Boolean` Aranan Case biçimi kullanıldığında değerlendirilen ifadedir.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="2cf0c-117">`Boolean_expression` geçerli bir `Boolean` ifadedir.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cf0c-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2cf0c-118">Return Value</span></span>  

 <span data-ttu-id="2cf0c-119">İçindeki tür kümesinden en yüksek öncelik türünü, `result_expression` ve isteğe bağlı olarak döndürür `else_result_expression` .</span><span class="sxs-lookup"><span data-stu-id="2cf0c-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cf0c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cf0c-120">Remarks</span></span>  

 <span data-ttu-id="2cf0c-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Case Ifadesi Transact-SQL Case ifadesine benzer.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="2cf0c-122">Hangi ifadenin uygun sonucu olacağını belirleyen bir dizi koşullu test oluşturmak için Case ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="2cf0c-123">Case ifadesinin bu biçimi, `Boolean` doğru sonuç ifadesini belirlemekte bir veya daha fazla ifadeye yönelik bir dizi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="2cf0c-124">CASE işlevi, `Boolean_expression` belirtilen sırada her bir yan tümce için değerlendirilir ve öğesini `result_expression` değerlendiren ilk döndürür `Boolean_expression` `true` .</span><span class="sxs-lookup"><span data-stu-id="2cf0c-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="2cf0c-125">Kalan ifadeler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="2cf0c-126">Hiçbir `Boolean_expression` değerlendirme yoksa `true` , veritabanı altyapısı `else_result_expression` Eğer bir else yan TÜMCESI belirtilmişse veya else yan tümcesi belirtilmemişse null değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="2cf0c-127">CASE deyimleri bir çoklu küme döndüremez.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cf0c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cf0c-128">Example</span></span>  

 <span data-ttu-id="2cf0c-129">Aşağıdaki Entity SQL sorgusu, `Boolean` sonucu tespit etmek için bir dizi ifadeyi değerlendirmek üzere Case ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="2cf0c-130">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2cf0c-131">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2cf0c-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2cf0c-132">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="2cf0c-133">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="2cf0c-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="2cf0c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cf0c-134">See also</span></span>

- [<span data-ttu-id="2cf0c-135">NI</span><span class="sxs-lookup"><span data-stu-id="2cf0c-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="2cf0c-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="2cf0c-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="2cf0c-137">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2cf0c-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
