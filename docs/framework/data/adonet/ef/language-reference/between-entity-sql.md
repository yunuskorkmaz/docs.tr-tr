---
title: "(Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ab5c08dad5f11d968eec4efa51ff225d3cfd0fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="between-entity-sql"></a><span data-ttu-id="6bb6a-102">(Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="6bb6a-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="6bb6a-103">Belirtilen aralıktaki bir değere bir ifade sonucu olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="6bb6a-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Arasındaki deyim arasında Transact-SQL ifadesi aynı işlevleri vardır.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb6a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bb6a-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="6bb6a-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="6bb6a-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6bb6a-107">Tarafından tanımlanan aralıktaki sınamak için herhangi bir geçerli ifadeler `begin_expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="6bb6a-108">`expression`her ikisi de aynı türde olmalıdır `begin_expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="6bb6a-109">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-109">Any valid expression.</span></span> <span data-ttu-id="6bb6a-110">`begin_expression`her ikisi de aynı türde olmalıdır `expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="6bb6a-111">`begin_expression`olmalıdır değerinden `end_expression`, dönüş değeri tasarruflarını Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="6bb6a-112">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-112">Any valid expression.</span></span> <span data-ttu-id="6bb6a-113">`end_expression`her ikisi de aynı türde olmalıdır `expression` ve `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="6bb6a-114">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="6bb6a-114">NOT</span></span>  
 <span data-ttu-id="6bb6a-115">BETWEEN sonucunu tasarruflarını gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="6bb6a-116">AND</span><span class="sxs-lookup"><span data-stu-id="6bb6a-116">AND</span></span>  
 <span data-ttu-id="6bb6a-117">Gösteren yer tutucu olarak davranan `expression` tarafından belirtilen aralıkta olmalıdır `begin_expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bb6a-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6bb6a-118">Return Value</span></span>  
 <span data-ttu-id="6bb6a-119">`true`varsa `expression` tarafından belirtilen aralık arasında `begin_expression` ve `end_expression`; Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="6bb6a-120">`null`olursa döndürülür `expression` olan `null` veya `begin_expression` veya `end_expression` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bb6a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bb6a-121">Remarks</span></span>  
 <span data-ttu-id="6bb6a-122">Özel bir aralık belirtmek için yerine BETWEEN büyüktür (>) ve küçük (<) işleçleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bb6a-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="6bb6a-123">Example</span></span>  
 <span data-ttu-id="6bb6a-124">ARASINDA bir değer belirli bir aralık içinde bir ifade sonuçlanıp sonuçlanmayacağını belirlemek için işleci aşağıdaki varlık SQL sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="6bb6a-125">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6bb6a-126">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="6bb6a-126">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6bb6a-127">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6bb6a-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6bb6a-128">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="6bb6a-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="6bb6a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6bb6a-129">See Also</span></span>  
 [<span data-ttu-id="6bb6a-130">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6bb6a-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
