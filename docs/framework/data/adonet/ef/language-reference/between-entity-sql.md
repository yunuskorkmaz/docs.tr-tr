---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 41036e629837bd5861368df545bed9423eac5b23
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251293"
---
# <a name="between-entity-sql"></a><span data-ttu-id="4d048-102">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4d048-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="4d048-103">Bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="4d048-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="4d048-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Between ifadesi, Transact-SQL between ifadesiyle aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4d048-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d048-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d048-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="4d048-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4d048-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4d048-107">`begin_expression` Ve`end_expression`tarafından tanımlanan aralıkta test edilecek geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="4d048-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="4d048-108">`expression`hem `begin_expression` hem de ile `end_expression`aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d048-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="4d048-109">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="4d048-109">Any valid expression.</span></span> <span data-ttu-id="4d048-110">`begin_expression`hem `expression` hem de ile `end_expression`aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d048-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="4d048-111">`begin_expression`Şundan `end_expression`küçük olmalıdır, aksi takdirde dönüş değeri de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d048-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="4d048-112">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="4d048-112">Any valid expression.</span></span> <span data-ttu-id="4d048-113">`end_expression`hem `expression` hem de ile `begin_expression`aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d048-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="4d048-114">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="4d048-114">NOT</span></span>  
 <span data-ttu-id="4d048-115">ARASıNDAKI sonucun nelenmiş olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d048-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="4d048-116">AND</span><span class="sxs-lookup"><span data-stu-id="4d048-116">AND</span></span>  
 <span data-ttu-id="4d048-117">, Ve `expression` tarafından`end_expression`belirtilen aralık dahilinde olması gerektiğini belirten bir yer tutucu görevi görür. `begin_expression`</span><span class="sxs-lookup"><span data-stu-id="4d048-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d048-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d048-118">Return Value</span></span>  
 <span data-ttu-id="4d048-119">`true`, ve `begin_expression`ilebelirtilen Aralık arasındaysa; Aksi takdirde, `false`. `expression` `end_expression`</span><span class="sxs-lookup"><span data-stu-id="4d048-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="4d048-120">`null``expression` , veya`null` ise,`null`döndürülür. `begin_expression` `end_expression`</span><span class="sxs-lookup"><span data-stu-id="4d048-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d048-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d048-121">Remarks</span></span>  
 <span data-ttu-id="4d048-122">Özel bir Aralık belirtmek için BETWEEN (>) ve küçüktür (<) işleçlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4d048-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d048-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d048-123">Example</span></span>  
 <span data-ttu-id="4d048-124">Aşağıdaki Entity SQL sorgusu, bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını anlamak için BETWEEN işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4d048-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="4d048-125">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="4d048-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4d048-126">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="4d048-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4d048-127">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="4d048-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4d048-128">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="4d048-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="4d048-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d048-129">See also</span></span>

- [<span data-ttu-id="4d048-130">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4d048-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
