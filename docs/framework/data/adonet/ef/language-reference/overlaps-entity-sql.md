---
title: Çakışma (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: f0c5d79b437ff06603ea10404357aa0b3270bc53
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150784"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="23e50-102">Çakışma (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="23e50-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="23e50-103">İki koleksiyon ortak öğeler sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="23e50-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e50-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23e50-104">Syntax</span></span>  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="23e50-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="23e50-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="23e50-106">Başka bir sorgu ifadesinden döndürülen koleksiyon karşılaştırmak için bir koleksiyon döndürür herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="23e50-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="23e50-107">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `expression`.</span><span class="sxs-lookup"><span data-stu-id="23e50-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23e50-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23e50-108">Return Value</span></span>  
 <span data-ttu-id="23e50-109">`true` iki koleksiyon ortak öğeler varsa, Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="23e50-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23e50-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23e50-110">Remarks</span></span>  
 <span data-ttu-id="23e50-111">İşlevsel olarak eşdeğerdir aşağıdaki ÇAKIŞAN sağlar:</span><span class="sxs-lookup"><span data-stu-id="23e50-111">OVERLAPS provides functionally equivalent to the following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="23e50-112">ÇAKIŞAN biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="23e50-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="23e50-113">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="23e50-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="23e50-114">Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="23e50-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23e50-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="23e50-115">Example</span></span>  
 <span data-ttu-id="23e50-116">Aşağıdaki varlık SQL sorgusu ÇAKIŞIYOR işleci belirler için iki koleksiyon ortak değerine sahip olup olmadığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="23e50-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="23e50-117">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="23e50-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="23e50-118">Derleme ve bu çalıştırma için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="23e50-118">To compile and run this, follow these steps:</span></span>  
  
1.  <span data-ttu-id="23e50-119">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="23e50-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="23e50-120">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="23e50-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="23e50-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23e50-121">See Also</span></span>  
 [<span data-ttu-id="23e50-122">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="23e50-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
