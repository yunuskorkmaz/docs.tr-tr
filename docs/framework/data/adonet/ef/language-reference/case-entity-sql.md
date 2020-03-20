---
title: CASE (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58b21d3be8e13a0a2204a4fd6d355f734207c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150473"
---
# <a name="case-entity-sql"></a><span data-ttu-id="b56ae-102">CASE (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="b56ae-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="b56ae-103">Sonucu belirlemek için `Boolean` bir dizi ifadeyi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b56ae-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b56ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b56ae-104">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="b56ae-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="b56ae-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="b56ae-106">Birden çok WHEN `Boolean_expression` THEN `result_expression` yan tümcelerinin kullanılabileceğini gösteren bir yer tutucudur.</span><span class="sxs-lookup"><span data-stu-id="b56ae-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="b56ae-107">Sonra`result_expression`</span><span class="sxs-lookup"><span data-stu-id="b56ae-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="b56ae-108">Değerlendirildiğinde `Boolean_expression` ifade döndürülür `true`mü?</span><span class="sxs-lookup"><span data-stu-id="b56ae-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="b56ae-109">`result expression`geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="b56ae-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="b56ae-110">Başka`else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="b56ae-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="b56ae-111">Hiçbir karşılaştırma işlemi değerlendirilmezse ifade `true`döndürülür mü.</span><span class="sxs-lookup"><span data-stu-id="b56ae-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="b56ae-112">Bu bağımsız değişken atlanırsa ve hiçbir karşılaştırma `true`işlemi değerlendirirse , CASE null döndürür.</span><span class="sxs-lookup"><span data-stu-id="b56ae-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="b56ae-113">`else_result_expression`geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="b56ae-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="b56ae-114">Veri türleri `else_result_expression` ve `result_expression` herhangi bir örtük bir dönüştürme aynı veya olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b56ae-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="b56ae-115">Tesis`Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="b56ae-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="b56ae-116">`Boolean` Aranan CASE biçimi kullanıldığında ifade değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b56ae-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="b56ae-117">`Boolean_expression`geçerli `Boolean` bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="b56ae-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b56ae-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b56ae-118">Return Value</span></span>  
 <span data-ttu-id="b56ae-119">Ve isteğe bağlı `result_expression` `else_result_expression`tür kümesinden en yüksek öncelik türünü verir.</span><span class="sxs-lookup"><span data-stu-id="b56ae-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b56ae-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b56ae-120">Remarks</span></span>  
 <span data-ttu-id="b56ae-121">Büyük/küçük [!INCLUDE[esql](../../../../../../includes/esql-md.md)] harf ifadesi Transact-SQL büyük/küçük harf ifadesini benzer.</span><span class="sxs-lookup"><span data-stu-id="b56ae-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="b56ae-122">Hangi ifadenin uygun sonucu vereceğini belirlemek için bir dizi koşullu test yapmak için servis talebi ifadesini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b56ae-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="b56ae-123">Bu servis talebi ifadesi biçimi, doğru sonucu `Boolean` ortaya çıkan ifadeyi belirlemek için bir veya daha fazla ifade dizisi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b56ae-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="b56ae-124">CASE işlevi belirtilen `Boolean_expression` sırada her WHEN yan tümcesi `Boolean_expression` için değerlendirir `true`ve `result_expression` ilk in 'e göre değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b56ae-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="b56ae-125">Kalan ifadeler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="b56ae-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="b56ae-126">Hiçbir `Boolean_expression` değerlendirme yoksa `true`, Veritabanı Altyapısı `else_result_expression` eğer bir ELSE yan tümcesi belirtilirse döndürür veya ELSE yan tümcesi belirtilmemişse null değeri.</span><span class="sxs-lookup"><span data-stu-id="b56ae-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="b56ae-127">CASE deyimi çok set döndüremez.</span><span class="sxs-lookup"><span data-stu-id="b56ae-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b56ae-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="b56ae-128">Example</span></span>  
 <span data-ttu-id="b56ae-129">Aşağıdaki Entity SQL sorgusu, sonucu belirlemek için `Boolean` bir dizi ifadeyi değerlendirmek için CASE ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b56ae-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="b56ae-130">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b56ae-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b56ae-131">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b56ae-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b56ae-132">[İlkel Tip Sonuçlarını Döndüren Bir Sorguyu Yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md): Nasıl Yapılır'daki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="b56ae-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="b56ae-133">Aşağıdaki sorguyu bağımsız değişken `ExecutePrimitiveTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="b56ae-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="b56ae-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b56ae-134">See also</span></span>

- [<span data-ttu-id="b56ae-135">Sonra</span><span class="sxs-lookup"><span data-stu-id="b56ae-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="b56ae-136">Seçin</span><span class="sxs-lookup"><span data-stu-id="b56ae-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="b56ae-137">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b56ae-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
