---
title: UNION (varlık SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 736b92f7aac89c309b37a8ac61a295c8d1495d6b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323297"
---
# <a name="union-entity-sql"></a><span data-ttu-id="17bff-102">UNION (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="17bff-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="17bff-103">İki veya daha fazla sorguların sonuçlarını tek bir koleksiyon birleştirir.</span><span class="sxs-lookup"><span data-stu-id="17bff-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17bff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17bff-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="17bff-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="17bff-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="17bff-106">Tüm ifadeler koleksiyon ile birleştirmek için bir koleksiyon döndüren herhangi bir geçerli sorgu ifade aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `expression`.</span><span class="sxs-lookup"><span data-stu-id="17bff-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="17bff-107">UNION</span><span class="sxs-lookup"><span data-stu-id="17bff-107">UNION</span></span>  
 <span data-ttu-id="17bff-108">Birden çok koleksiyon birleştirilir ve tek bir koleksiyon döndürülen olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="17bff-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="17bff-109">TÜM</span><span class="sxs-lookup"><span data-stu-id="17bff-109">ALL</span></span>  
 <span data-ttu-id="17bff-110">Birden çok koleksiyon birleştirilir ve yinelenenler de dahil olmak üzere tek bir koleksiyon döndürülen olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="17bff-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="17bff-111">Belirtilmezse, çoğaltmaları sonucu koleksiyondan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="17bff-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17bff-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="17bff-112">Return Value</span></span>  
 <span data-ttu-id="17bff-113">Bir koleksiyonu aynı türde veya ortak bir temel veya türetilmiş tür `expression`.</span><span class="sxs-lookup"><span data-stu-id="17bff-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17bff-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17bff-114">Remarks</span></span>  
 <span data-ttu-id="17bff-115">BİRLEŞİM biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="17bff-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="17bff-116">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="17bff-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="17bff-117">Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="17bff-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17bff-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="17bff-118">Example</span></span>  
 <span data-ttu-id="17bff-119">Aşağıdaki varlık SQL sorgusu UNION ALL işleci iki sorgunun sonuçlarını tek bir koleksiyona birleştirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="17bff-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="17bff-120">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="17bff-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="17bff-121">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="17bff-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="17bff-122">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="17bff-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="17bff-123">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="17bff-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="17bff-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17bff-124">See also</span></span>

- [<span data-ttu-id="17bff-125">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="17bff-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
