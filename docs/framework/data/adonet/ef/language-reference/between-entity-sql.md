---
description: 'Hakkında daha fazla bilgi edinin: BETWEEN (Entity SQL)'
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 35ac16e94f2e55f6a0f76591daf0f91f9708aa53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697120"
---
# <a name="between-entity-sql"></a><span data-ttu-id="ae34f-103">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ae34f-103">BETWEEN (Entity SQL)</span></span>

<span data-ttu-id="ae34f-104">Bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ae34f-104">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="ae34f-105">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Between ifadesi, Transact-SQL between ifadesiyle aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ae34f-105">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae34f-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ae34f-106">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a><span data-ttu-id="ae34f-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ae34f-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="ae34f-108">Ve tarafından tanımlanan aralıkta test edilecek geçerli bir ifade `begin_expression` `end_expression` .</span><span class="sxs-lookup"><span data-stu-id="ae34f-108">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="ae34f-109">`expression` hem hem de ile aynı türde olmalıdır `begin_expression` `end_expression` .</span><span class="sxs-lookup"><span data-stu-id="ae34f-109">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="ae34f-110">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="ae34f-110">Any valid expression.</span></span> <span data-ttu-id="ae34f-111">`begin_expression` hem hem de ile aynı türde olmalıdır `expression` `end_expression` .</span><span class="sxs-lookup"><span data-stu-id="ae34f-111">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="ae34f-112">`begin_expression` Şundan küçük olmalıdır `end_expression` , aksi takdirde dönüş değeri de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ae34f-112">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="ae34f-113">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="ae34f-113">Any valid expression.</span></span> <span data-ttu-id="ae34f-114">`end_expression` hem hem de ile aynı türde olmalıdır `expression` `begin_expression` .</span><span class="sxs-lookup"><span data-stu-id="ae34f-114">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="ae34f-115">NOT</span><span class="sxs-lookup"><span data-stu-id="ae34f-115">NOT</span></span>  
 <span data-ttu-id="ae34f-116">ARASıNDAKI sonucun nelenmiş olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae34f-116">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="ae34f-117">AND</span><span class="sxs-lookup"><span data-stu-id="ae34f-117">AND</span></span>  
 <span data-ttu-id="ae34f-118">, `expression` Ve tarafından belirtilen aralık dahilinde olması gerektiğini belirten bir yer tutucu görevi `begin_expression` görür `end_expression` .</span><span class="sxs-lookup"><span data-stu-id="ae34f-118">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae34f-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae34f-119">Return Value</span></span>  

 <span data-ttu-id="ae34f-120">`true` , `expression` ve ile belirtilen Aralık arasındaysa `begin_expression` `end_expression` ; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="ae34f-120">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="ae34f-121">`null` , veya ise, `expression` döndürülür `null` `begin_expression` `end_expression` `null` .</span><span class="sxs-lookup"><span data-stu-id="ae34f-121">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae34f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae34f-122">Remarks</span></span>  

 <span data-ttu-id="ae34f-123">Özel bir Aralık belirtmek için BETWEEN (>) ve küçüktür (<) işleçlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae34f-123">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae34f-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae34f-124">Example</span></span>  

 <span data-ttu-id="ae34f-125">Aşağıdaki Entity SQL sorgusu, bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını anlamak için BETWEEN işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae34f-125">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="ae34f-126">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="ae34f-126">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ae34f-127">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ae34f-127">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ae34f-128">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="ae34f-128">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ae34f-129">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="ae34f-129">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="ae34f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae34f-130">See also</span></span>

- [<span data-ttu-id="ae34f-131">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ae34f-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
