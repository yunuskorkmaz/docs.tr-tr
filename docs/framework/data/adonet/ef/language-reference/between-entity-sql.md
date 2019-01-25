---
title: (Varlık arasında SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: cface8ab50e53f21293ad54ea6961c7e308080b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690702"
---
# <a name="between-entity-sql"></a><span data-ttu-id="429d6-102">(Varlık arasında SQL)</span><span class="sxs-lookup"><span data-stu-id="429d6-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="429d6-103">Bir ifadenin belirtilen bir aralıktaki bir değer sonuçlanıp sonuçlanmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="429d6-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="429d6-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN ifadesi arasında Transact-SQL deyimi ile aynı işlevlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="429d6-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="429d6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="429d6-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="429d6-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="429d6-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="429d6-107">Tarafından tanımlanan aralıkta test etmek için herhangi bir geçerli ifade `begin_expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="429d6-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="429d6-108">`expression` her ikisi de aynı türde olmalıdır `begin_expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="429d6-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="429d6-109">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="429d6-109">Any valid expression.</span></span> <span data-ttu-id="429d6-110">`begin_expression` her ikisi de aynı türde olmalıdır `expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="429d6-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="429d6-111">`begin_expression` olmalıdır küçüktür `end_expression`, dönüş değerine değilleme Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="429d6-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="429d6-112">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="429d6-112">Any valid expression.</span></span> <span data-ttu-id="429d6-113">`end_expression` her ikisi de aynı türde olmalıdır `expression` ve `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="429d6-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="429d6-114">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="429d6-114">NOT</span></span>  
 <span data-ttu-id="429d6-115">BETWEEN sonucunu negatif olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="429d6-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="429d6-116">AND</span><span class="sxs-lookup"><span data-stu-id="429d6-116">AND</span></span>  
 <span data-ttu-id="429d6-117">Gösteren bir yer tutucu olarak görev yapar `expression` tarafından belirtilen aralığı içinde olmalıdır `begin_expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="429d6-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="429d6-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="429d6-118">Return Value</span></span>  
 <span data-ttu-id="429d6-119">`true` varsa `expression` tarafından belirtilen aralık arasında `begin_expression` ve `end_expression`; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="429d6-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="429d6-120">`null` ise döndürülecek `expression` olduğu `null` veya `begin_expression` veya `end_expression` olduğu `null`.</span><span class="sxs-lookup"><span data-stu-id="429d6-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="429d6-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="429d6-121">Remarks</span></span>  
 <span data-ttu-id="429d6-122">Özel bir aralık belirtmek için BETWEEN yerine büyüktür (>) ve küçüktür (<) işleçlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="429d6-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="429d6-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="429d6-123">Example</span></span>  
 <span data-ttu-id="429d6-124">ARASINDA işleci bir ifade değeri belirtilen bir aralıktaki sonuçlanıp sonuçlanmayacağını belirlemek için aşağıdaki varlık SQL sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="429d6-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="429d6-125">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="429d6-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="429d6-126">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="429d6-126">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="429d6-127">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="429d6-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="429d6-128">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="429d6-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="429d6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="429d6-129">See also</span></span>
- [<span data-ttu-id="429d6-130">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="429d6-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
