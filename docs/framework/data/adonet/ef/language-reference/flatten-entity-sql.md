---
description: ': DÜZLEŞTIR (Entity SQL) hakkında daha fazla bilgi'
title: DÜZLEŞTIR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 3701fbdf481024c799b4cdc6f109bae9fc226609
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786361"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="2a800-103">DÜZLEŞTIR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2a800-103">FLATTEN (Entity SQL)</span></span>

<span data-ttu-id="2a800-104">Bir koleksiyon koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2a800-104">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="2a800-105">Yeni koleksiyon eski koleksiyonla aynı öğeleri, ancak iç içe bir yapı olmadan içerir.</span><span class="sxs-lookup"><span data-stu-id="2a800-105">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a800-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2a800-106">Syntax</span></span>  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="2a800-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2a800-107">Arguments</span></span>  

 `collection`  
 <span data-ttu-id="2a800-108">Tek bir koleksiyonda düzleştirmek için bir değer koleksiyonları koleksiyonu döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="2a800-108">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a800-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a800-109">Remarks</span></span>  

 <span data-ttu-id="2a800-110">`FLATTEN` , [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="2a800-110">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="2a800-111">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2a800-111">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="2a800-112">Bkz. set işleçleri için öncelik bilgileri [hariç](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2a800-112">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a800-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a800-113">Example</span></span>  

 <span data-ttu-id="2a800-114">Aşağıdaki Entity SQL sorgusu, bir koleksiyon `FLATTEN` koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürmek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a800-114">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="2a800-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2a800-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2a800-116">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2a800-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2a800-117">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="2a800-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="2a800-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a800-118">See also</span></span>

- [<span data-ttu-id="2a800-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2a800-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
