---
title: "Durum (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9afc5e3bbf8e6fe732aca9e65c8ba5bd5f620c85
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="case-entity-sql"></a><span data-ttu-id="172eb-102">Durum (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="172eb-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="172eb-103">Bir dizi değerlendirir `Boolean` sonucu belirlemek için ifadeler.</span><span class="sxs-lookup"><span data-stu-id="172eb-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="172eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="172eb-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="172eb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="172eb-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="172eb-106">Bu çoklu gösteren bir yer tutucudur zaman `Boolean_expression` sonra `result_expression` yan tümceleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="172eb-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="172eb-107">ARDINDAN`result_expression`</span><span class="sxs-lookup"><span data-stu-id="172eb-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="172eb-108">İfade ne zaman döndürülür `Boolean_expression` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="172eb-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="172eb-109">`result expression`Geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="172eb-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="172eb-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="172eb-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="172eb-111">İfade karşılaştırma işlemi için hesaplar, döndürülen `true`.</span><span class="sxs-lookup"><span data-stu-id="172eb-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="172eb-112">Bu bağımsız değişkeni boş bırakılırsa ve karşılaştırma işlemi değerlendiren `true`, servis talebi null döndürür.</span><span class="sxs-lookup"><span data-stu-id="172eb-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="172eb-113">`else_result_expression`Geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="172eb-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="172eb-114">Veri türlerini `else_result_expression` ve tüm `result_expression` örtük bir dönüştürme olmalıdır veya aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="172eb-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="172eb-115">NE ZAMAN`Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="172eb-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="172eb-116">Olan `Boolean` Aranan servis talebi biçimi kullanıldığında değerlendirilen ifade.</span><span class="sxs-lookup"><span data-stu-id="172eb-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="172eb-117">`Boolean_expression`Tüm geçerli `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="172eb-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="172eb-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="172eb-118">Return Value</span></span>  
 <span data-ttu-id="172eb-119">En yüksek öncelik türüyle türlerinde kümesinden döndürür `result_expression` ve isteğe bağlı `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="172eb-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="172eb-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="172eb-120">Remarks</span></span>  
 <span data-ttu-id="172eb-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Servis talebi ifade benzer [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] durumda ifade.</span><span class="sxs-lookup"><span data-stu-id="172eb-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case expression.</span></span> <span data-ttu-id="172eb-122">Case deyimi, bir dizi hangi ifade uygun sonucu verecek olan belirlemek için koşullu test yapmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="172eb-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="172eb-123">Bir dizi bir veya daha fazla bilgi için bu formu servis talebi ifadesinin geçerlidir `Boolean` doğru elde edilen ifadesi belirlemek için deyimleri.</span><span class="sxs-lookup"><span data-stu-id="172eb-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="172eb-124">Durum işlevi değerlendirir `Boolean_expression` her zaman yan tümcesi sırada belirtilen ve döndürür `result_expression` ilk `Boolean_expression` , hesaplar için `true`.</span><span class="sxs-lookup"><span data-stu-id="172eb-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="172eb-125">Kalan ifadeler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="172eb-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="172eb-126">Yoksa `Boolean_expression` değerlendiren `true`, veritabanı altyapısı döndürür `else_result_expression` ELSE yan tümcesinin belirtilmişse veya hiçbir ELSE yan tümcesi belirtilmişse, bir null değer.</span><span class="sxs-lookup"><span data-stu-id="172eb-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="172eb-127">CASE deyimi bir çoklu küme döndüremez.</span><span class="sxs-lookup"><span data-stu-id="172eb-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="172eb-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="172eb-128">Example</span></span>  
 <span data-ttu-id="172eb-129">Bir dizi değerlendirmek için büyük/küçük HARFE ifade aşağıdaki varlık SQL sorgusunu kullanır `Boolean` sonucu belirlemek için ifadeler.</span><span class="sxs-lookup"><span data-stu-id="172eb-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="172eb-130">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="172eb-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="172eb-131">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="172eb-131">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="172eb-132">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="172eb-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="172eb-133">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="172eb-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="172eb-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="172eb-134">See Also</span></span>  
 [<span data-ttu-id="172eb-135">THEN</span><span class="sxs-lookup"><span data-stu-id="172eb-135">THEN</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)  
 [<span data-ttu-id="172eb-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="172eb-136">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="172eb-137">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="172eb-137">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
