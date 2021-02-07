---
description: 'Daha fazla bilgi edinin: ıNTERSECT (Entity SQL)'
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 45c0434f6fc0ed6c110162d7e34d76c336635b0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748525"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="bea6c-103">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bea6c-103">INTERSECT (Entity SQL)</span></span>

<span data-ttu-id="bea6c-104">INTERSECT işleneninin sol ve sağ taraflarındaki sorgu ifadeleri tarafından döndürülen ayrı değerlerin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bea6c-104">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="bea6c-105">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türde olmalıdır `expression` .</span><span class="sxs-lookup"><span data-stu-id="bea6c-105">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea6c-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bea6c-106">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="bea6c-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="bea6c-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="bea6c-108">Başka bir sorgu ifadesinden döndürülen koleksiyonla karşılaştırmak için bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="bea6c-108">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bea6c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bea6c-109">Return Value</span></span>  

 <span data-ttu-id="bea6c-110">Aynı türde veya ortak bir temel ya da türetilmiş türden bir koleksiyon `expression` .</span><span class="sxs-lookup"><span data-stu-id="bea6c-110">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bea6c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bea6c-111">Remarks</span></span>  

 <span data-ttu-id="bea6c-112">INTERSECT, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="bea6c-112">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="bea6c-113">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bea6c-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="bea6c-114">Set işleçleri için öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bkz. [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="bea6c-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bea6c-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="bea6c-115">Example</span></span>  

 <span data-ttu-id="bea6c-116">Aşağıdaki Entity SQL sorgusu, ıNTERSECT işleneninin sol ve sağ taraflarındaki sorgu ifadeleri tarafından döndürülen ayrı değerlerin bir koleksiyonunu döndürmek için ıNTERSECT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bea6c-116">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="bea6c-117">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="bea6c-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bea6c-118">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bea6c-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bea6c-119">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="bea6c-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bea6c-120">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="bea6c-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="bea6c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bea6c-121">See also</span></span>

- [<span data-ttu-id="bea6c-122">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bea6c-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
