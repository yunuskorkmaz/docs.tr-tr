---
title: INTERSECT (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 2fe7a9610863efab9fd332c40f7a644cd5c07e35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595961"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="e87e0-102">INTERSECT (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e87e0-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="e87e0-103">INTERSECT işlecinin sol tarafında soldaki iki sorgu ifadeleri tarafından döndürülen herhangi ayrı değerlerin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e87e0-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="e87e0-104">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `expression`.</span><span class="sxs-lookup"><span data-stu-id="e87e0-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e87e0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e87e0-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e87e0-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e87e0-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e87e0-107">Başka bir sorgu ifadesinden döndürülen koleksiyon karşılaştırmak için bir koleksiyon döndürür herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="e87e0-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e87e0-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e87e0-108">Return Value</span></span>  
 <span data-ttu-id="e87e0-109">Bir koleksiyonu aynı türde veya ortak bir temel veya türetilmiş tür `expression`.</span><span class="sxs-lookup"><span data-stu-id="e87e0-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e87e0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e87e0-110">Remarks</span></span>  
 <span data-ttu-id="e87e0-111">INTERSECT biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e87e0-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="e87e0-112">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e87e0-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="e87e0-113">Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e87e0-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e87e0-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e87e0-114">Example</span></span>  
 <span data-ttu-id="e87e0-115">Aşağıdaki varlık SQL sorgusu, soldaki iki sorgu ifadeleri tarafından döndürülen herhangi ayrı değerlerin bir koleksiyonunu ve INTERSECT işlecinin sol tarafında döndürülecek INTERSECT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e87e0-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="e87e0-116">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="e87e0-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e87e0-117">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="e87e0-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e87e0-118">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e87e0-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e87e0-119">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e87e0-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="e87e0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e87e0-120">See also</span></span>
- [<span data-ttu-id="e87e0-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e87e0-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
