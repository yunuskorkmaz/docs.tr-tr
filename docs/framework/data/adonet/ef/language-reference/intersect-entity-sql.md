---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: a943de89de37d00cc2a643b443da7ef1fd3380b9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250596"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="0bef5-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0bef5-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="0bef5-103">INTERSECT işleneninin sol ve sağ taraflarındaki sorgu ifadeleri tarafından döndürülen ayrı değerlerin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="0bef5-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="0bef5-104">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde `expression`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bef5-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bef5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bef5-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0bef5-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="0bef5-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0bef5-107">Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="0bef5-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bef5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0bef5-108">Return Value</span></span>  
 <span data-ttu-id="0bef5-109">Aynı türde veya ortak bir temel ya da türetilmiş türden `expression`bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="0bef5-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bef5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0bef5-110">Remarks</span></span>  
 <span data-ttu-id="0bef5-111">Intersect, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="0bef5-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="0bef5-112">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0bef5-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="0bef5-113">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Set işleçleri için öncelik bilgileri için bkz. [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0bef5-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bef5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bef5-114">Example</span></span>  
 <span data-ttu-id="0bef5-115">Aşağıdaki Entity SQL sorgusu, ıNTERSECT işleneninin sol ve sağ taraflarındaki sorgu ifadeleri tarafından döndürülen ayrı değerlerin bir koleksiyonunu döndürmek için ıNTERSECT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0bef5-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="0bef5-116">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="0bef5-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0bef5-117">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0bef5-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0bef5-118">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="0bef5-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0bef5-119">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="0bef5-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="0bef5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bef5-120">See also</span></span>

- [<span data-ttu-id="0bef5-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0bef5-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
