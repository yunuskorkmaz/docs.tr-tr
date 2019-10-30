---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 611e90f362bbc0eac521e1e1998fb85200169c19
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039942"
---
# <a name="between-entity-sql"></a><span data-ttu-id="4d06c-102">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4d06c-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="4d06c-103">Bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="4d06c-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="4d06c-104">İfade ARASıNDAKI [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Transact-SQL BETWEEN ifadesiyle aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4d06c-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d06c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d06c-105">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="4d06c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4d06c-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4d06c-107">`begin_expression` ve `end_expression`tarafından tanımlanan aralıkta test edilecek geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="4d06c-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="4d06c-108">`expression`, `begin_expression` ve `end_expression`aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d06c-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="4d06c-109">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="4d06c-109">Any valid expression.</span></span> <span data-ttu-id="4d06c-110">`begin_expression`, `expression` ve `end_expression`aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d06c-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="4d06c-111">`begin_expression` `end_expression`küçük olmalıdır, aksi takdirde dönüş değeri de kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="4d06c-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="4d06c-112">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="4d06c-112">Any valid expression.</span></span> <span data-ttu-id="4d06c-113">`end_expression`, `expression` ve `begin_expression`aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d06c-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="4d06c-114">BAŞLATıLMADı</span><span class="sxs-lookup"><span data-stu-id="4d06c-114">NOT</span></span>  
 <span data-ttu-id="4d06c-115">ARASıNDAKI sonucun nelenmiş olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d06c-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="4d06c-116">AND</span><span class="sxs-lookup"><span data-stu-id="4d06c-116">AND</span></span>  
 <span data-ttu-id="4d06c-117">`expression`, `begin_expression` ve `end_expression`belirtilen aralık dahilinde olması gerektiğini belirten bir yer tutucu görevi görür.</span><span class="sxs-lookup"><span data-stu-id="4d06c-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d06c-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d06c-118">Return Value</span></span>  
 <span data-ttu-id="4d06c-119">`expression`, `begin_expression` ve `end_expression`tarafından belirtilen Aralık arasında ise `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="4d06c-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="4d06c-120">`null`, `expression` `null` ya da `begin_expression` veya `end_expression` `null`ise döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4d06c-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d06c-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d06c-121">Remarks</span></span>  
 <span data-ttu-id="4d06c-122">Özel bir Aralık belirtmek için BETWEEN (>) ve küçüktür (<) işleçlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4d06c-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d06c-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d06c-123">Example</span></span>  
 <span data-ttu-id="4d06c-124">Aşağıdaki Entity SQL sorgusu, bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını anlamak için BETWEEN işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4d06c-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="4d06c-125">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="4d06c-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4d06c-126">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="4d06c-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4d06c-127">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="4d06c-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4d06c-128">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="4d06c-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="4d06c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d06c-129">See also</span></span>

- [<span data-ttu-id="4d06c-130">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4d06c-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
