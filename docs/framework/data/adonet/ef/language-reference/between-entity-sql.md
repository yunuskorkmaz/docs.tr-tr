---
title: (Varlık arasında SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 2c411fd7fcac9d98323d5fcfb1874f98bc664991
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225267"
---
# <a name="between-entity-sql"></a><span data-ttu-id="be129-102">(Varlık arasında SQL)</span><span class="sxs-lookup"><span data-stu-id="be129-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="be129-103">Bir ifadenin belirtilen bir aralıktaki bir değer sonuçlanıp sonuçlanmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="be129-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="be129-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN ifadesi arasında Transact-SQL deyimi ile aynı işlevlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="be129-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be129-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be129-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="be129-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="be129-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="be129-107">Tarafından tanımlanan aralıkta test etmek için herhangi bir geçerli ifade `begin_expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="be129-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> `expression` <span data-ttu-id="be129-108">her ikisi de aynı türde olmalıdır `begin_expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="be129-108">must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="be129-109">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="be129-109">Any valid expression.</span></span> `begin_expression` <span data-ttu-id="be129-110">her ikisi de aynı türde olmalıdır `expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="be129-110">must be the same type as both `expression` and `end_expression`.</span></span> `begin_expression` <span data-ttu-id="be129-111">olmalıdır küçüktür `end_expression`, dönüş değerine değilleme Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="be129-111">should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="be129-112">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="be129-112">Any valid expression.</span></span> `end_expression` <span data-ttu-id="be129-113">her ikisi de aynı türde olmalıdır `expression` ve `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="be129-113">must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="be129-114">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="be129-114">NOT</span></span>  
 <span data-ttu-id="be129-115">BETWEEN sonucunu negatif olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="be129-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="be129-116">AND</span><span class="sxs-lookup"><span data-stu-id="be129-116">AND</span></span>  
 <span data-ttu-id="be129-117">Gösteren bir yer tutucu olarak görev yapar `expression` tarafından belirtilen aralığı içinde olmalıdır `begin_expression` ve `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="be129-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be129-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be129-118">Return Value</span></span>  
 `true` <span data-ttu-id="be129-119">varsa `expression` tarafından belirtilen aralık arasında `begin_expression` ve `end_expression`; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="be129-119">if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> `null` <span data-ttu-id="be129-120">ise döndürülecek `expression` olduğu `null` veya `begin_expression` veya `end_expression` olduğu `null`.</span><span class="sxs-lookup"><span data-stu-id="be129-120">will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be129-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be129-121">Remarks</span></span>  
 <span data-ttu-id="be129-122">Özel bir aralık belirtmek için BETWEEN yerine büyüktür (>) ve küçüktür (<) işleçlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="be129-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be129-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="be129-123">Example</span></span>  
 <span data-ttu-id="be129-124">ARASINDA işleci bir ifade değeri belirtilen bir aralıktaki sonuçlanıp sonuçlanmayacağını belirlemek için aşağıdaki varlık SQL sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="be129-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="be129-125">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="be129-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="be129-126">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="be129-126">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="be129-127">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="be129-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="be129-128">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="be129-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="be129-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be129-129">See also</span></span>

- [<span data-ttu-id="be129-130">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="be129-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
