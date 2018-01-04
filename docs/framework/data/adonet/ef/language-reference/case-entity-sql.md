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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: df86e69684a111effc29a2663d18310b276f4b83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="case-entity-sql"></a><span data-ttu-id="3d9a2-102">Durum (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="3d9a2-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="3d9a2-103">Bir dizi değerlendirir `Boolean` sonucu belirlemek için ifadeler.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d9a2-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d9a2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3d9a2-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="3d9a2-106">Bu çoklu gösteren bir yer tutucudur zaman `Boolean_expression` sonra `result_expression` yan tümceleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="3d9a2-107">ARDINDAN`result_expression`</span><span class="sxs-lookup"><span data-stu-id="3d9a2-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="3d9a2-108">İfade ne zaman döndürülür `Boolean_expression` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="3d9a2-109">`result expression`Geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="3d9a2-110">ELSE`else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="3d9a2-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="3d9a2-111">İfade karşılaştırma işlemi için hesaplar, döndürülen `true`.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="3d9a2-112">Bu bağımsız değişkeni boş bırakılırsa ve karşılaştırma işlemi değerlendiren `true`, servis talebi null döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="3d9a2-113">`else_result_expression`Geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="3d9a2-114">Veri türlerini `else_result_expression` ve tüm `result_expression` örtük bir dönüştürme olmalıdır veya aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="3d9a2-115">NE ZAMAN`Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="3d9a2-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="3d9a2-116">Olan `Boolean` Aranan servis talebi biçimi kullanıldığında değerlendirilen ifade.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="3d9a2-117">`Boolean_expression`Tüm geçerli `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d9a2-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d9a2-118">Return Value</span></span>  
 <span data-ttu-id="3d9a2-119">En yüksek öncelik türüyle türlerinde kümesinden döndürür `result_expression` ve isteğe bağlı `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d9a2-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d9a2-120">Remarks</span></span>  
 <span data-ttu-id="3d9a2-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Servis talebi ifade benzer [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] durumda ifade.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case expression.</span></span> <span data-ttu-id="3d9a2-122">Case deyimi, bir dizi hangi ifade uygun sonucu verecek olan belirlemek için koşullu test yapmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="3d9a2-123">Bir dizi bir veya daha fazla bilgi için bu formu servis talebi ifadesinin geçerlidir `Boolean` doğru elde edilen ifadesi belirlemek için deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="3d9a2-124">Durum işlevi değerlendirir `Boolean_expression` her zaman yan tümcesi sırada belirtilen ve döndürür `result_expression` ilk `Boolean_expression` , hesaplar için `true`.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="3d9a2-125">Kalan ifadeler değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="3d9a2-126">Yoksa `Boolean_expression` değerlendiren `true`, veritabanı altyapısı döndürür `else_result_expression` ELSE yan tümcesinin belirtilmişse veya hiçbir ELSE yan tümcesi belirtilmişse, bir null değer.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="3d9a2-127">CASE deyimi bir çoklu küme döndüremez.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d9a2-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d9a2-128">Example</span></span>  
 <span data-ttu-id="3d9a2-129">Bir dizi değerlendirmek için büyük/küçük HARFE ifade aşağıdaki varlık SQL sorgusunu kullanır `Boolean` sonucu belirlemek için ifadeler.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="3d9a2-130">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3d9a2-131">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="3d9a2-131">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3d9a2-132">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3d9a2-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="3d9a2-133">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3d9a2-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="3d9a2-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d9a2-134">See Also</span></span>  
 [<span data-ttu-id="3d9a2-135">THEN</span><span class="sxs-lookup"><span data-stu-id="3d9a2-135">THEN</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)  
 [<span data-ttu-id="3d9a2-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="3d9a2-136">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="3d9a2-137">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3d9a2-137">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
