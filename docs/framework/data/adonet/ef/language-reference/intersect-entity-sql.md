---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 217cd9b2a428c890d83d2b55d45321a04488398e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203650"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="ca31d-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ca31d-102">INTERSECT (Entity SQL)</span></span>

<span data-ttu-id="ca31d-103">INTERSECT işleneninin sol ve sağ taraflarındaki sorgu ifadeleri tarafından döndürülen ayrı değerlerin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca31d-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="ca31d-104">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde olmalıdır `expression` .</span><span class="sxs-lookup"><span data-stu-id="ca31d-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca31d-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ca31d-105">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ca31d-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ca31d-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="ca31d-107">Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="ca31d-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca31d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ca31d-108">Return Value</span></span>  

 <span data-ttu-id="ca31d-109">Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` .</span><span class="sxs-lookup"><span data-stu-id="ca31d-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca31d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca31d-110">Remarks</span></span>  

 <span data-ttu-id="ca31d-111">INTERSECT, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="ca31d-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ca31d-112">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ca31d-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ca31d-113">Set işleçleri için öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bkz. [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ca31d-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca31d-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca31d-114">Example</span></span>  

 <span data-ttu-id="ca31d-115">Aşağıdaki Entity SQL sorgusu, ıNTERSECT işleneninin sol ve sağ taraflarındaki sorgu ifadeleri tarafından döndürülen ayrı değerlerin bir koleksiyonunu döndürmek için ıNTERSECT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ca31d-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="ca31d-116">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="ca31d-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ca31d-117">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ca31d-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ca31d-118">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="ca31d-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ca31d-119">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="ca31d-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="ca31d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca31d-120">See also</span></span>

- [<span data-ttu-id="ca31d-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ca31d-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
