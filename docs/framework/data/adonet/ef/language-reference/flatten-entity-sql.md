---
title: DÜZLEŞTIR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 327a20bbc53566846e7d828f511bcd1d25cc5504
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250961"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="ca25c-102">DÜZLEŞTIR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ca25c-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="ca25c-103">Bir koleksiyon koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ca25c-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="ca25c-104">Yeni koleksiyon eski koleksiyonla aynı öğeleri, ancak iç içe bir yapı olmadan içerir.</span><span class="sxs-lookup"><span data-stu-id="ca25c-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca25c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca25c-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="ca25c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ca25c-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="ca25c-107">Tek bir koleksiyonda düzleştirmek için bir değer koleksiyonları koleksiyonu döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="ca25c-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca25c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca25c-108">Remarks</span></span>  
 <span data-ttu-id="ca25c-109">`FLATTEN`, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="ca25c-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ca25c-110">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ca25c-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ca25c-111">Bkz [](except-entity-sql.md) . [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçleri için öncelik bilgileri hariç.</span><span class="sxs-lookup"><span data-stu-id="ca25c-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca25c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca25c-112">Example</span></span>  
 <span data-ttu-id="ca25c-113">Aşağıdaki Entity SQL sorgusu, bir koleksiyon `FLATTEN` koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ca25c-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="ca25c-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ca25c-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ca25c-115">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="ca25c-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ca25c-116">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="ca25c-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="ca25c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca25c-117">See also</span></span>

- [<span data-ttu-id="ca25c-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ca25c-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
