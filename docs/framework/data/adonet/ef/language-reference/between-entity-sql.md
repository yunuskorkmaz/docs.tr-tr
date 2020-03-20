---
title: BETWEEN (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150499"
---
# <a name="between-entity-sql"></a><span data-ttu-id="9cecc-102">BETWEEN (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="9cecc-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="9cecc-103">İfadenin belirli bir aralıktaki bir değerle sonuçlanıp sonuçlaşmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9cecc-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="9cecc-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN ifadesi, Transact-SQL BETWEEN ifadesi ile aynı işlevsellik tesahiptir.</span><span class="sxs-lookup"><span data-stu-id="9cecc-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cecc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9cecc-105">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a><span data-ttu-id="9cecc-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="9cecc-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9cecc-107">Tarafından tanımlanan aralıkta test etmek `begin_expression` için `end_expression`geçerli bir ifade ve .</span><span class="sxs-lookup"><span data-stu-id="9cecc-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="9cecc-108">`expression`her ikisi `begin_expression` yle aynı `end_expression`türde olmalıdır ve .</span><span class="sxs-lookup"><span data-stu-id="9cecc-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="9cecc-109">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="9cecc-109">Any valid expression.</span></span> <span data-ttu-id="9cecc-110">`begin_expression`her ikisi `expression` yle aynı `end_expression`türde olmalıdır ve .</span><span class="sxs-lookup"><span data-stu-id="9cecc-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="9cecc-111">`begin_expression`daha `end_expression`az olmalıdır, aksi takdirde iade değeri inkar edilecektir.</span><span class="sxs-lookup"><span data-stu-id="9cecc-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="9cecc-112">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="9cecc-112">Any valid expression.</span></span> <span data-ttu-id="9cecc-113">`end_expression`her ikisi `expression` yle aynı `begin_expression`türde olmalıdır ve .</span><span class="sxs-lookup"><span data-stu-id="9cecc-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="9cecc-114">NOT</span><span class="sxs-lookup"><span data-stu-id="9cecc-114">NOT</span></span>  
 <span data-ttu-id="9cecc-115">BETWEEN sonucunun inkâr edilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cecc-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="9cecc-116">AND</span><span class="sxs-lookup"><span data-stu-id="9cecc-116">AND</span></span>  
 <span data-ttu-id="9cecc-117">Tarafından belirtilen aralıkta `expression` olması gerektiğini belirten bir `begin_expression` `end_expression`yer tutucu görevi görür.</span><span class="sxs-lookup"><span data-stu-id="9cecc-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cecc-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9cecc-118">Return Value</span></span>  
 <span data-ttu-id="9cecc-119">`true`tarafından `expression` `begin_expression` belirtilen aralık arasında `end_expression`ise ve ; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="9cecc-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="9cecc-120">`null`ise `expression` `null` veya ise `begin_expression` iade `end_expression` edilecektir. `null`</span><span class="sxs-lookup"><span data-stu-id="9cecc-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cecc-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9cecc-121">Remarks</span></span>  
 <span data-ttu-id="9cecc-122">Özel bir aralık belirtmek için, (>) ve (<) işleçlerden daha büyük olan işleçleri ARA ILE'den daha az kullanın.</span><span class="sxs-lookup"><span data-stu-id="9cecc-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cecc-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="9cecc-123">Example</span></span>  
 <span data-ttu-id="9cecc-124">Aşağıdaki Entity SQL sorgusu, bir ifadenin belirli bir aralıktaki bir değerle sonuçlanıp sonuçlanmadığını belirlemek için ARA Işleci'ni kullanır.</span><span class="sxs-lookup"><span data-stu-id="9cecc-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="9cecc-125">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9cecc-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9cecc-126">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9cecc-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9cecc-127">[YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="9cecc-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9cecc-128">Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="9cecc-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="9cecc-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cecc-129">See also</span></span>

- [<span data-ttu-id="9cecc-130">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9cecc-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
