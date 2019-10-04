---
title: DÜZLEŞTIR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 84b846e3db86c664bc42363f3d983a1001f5c318
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833815"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="d3312-102">DÜZLEŞTIR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d3312-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="d3312-103">Bir koleksiyon koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d3312-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="d3312-104">Yeni koleksiyon eski koleksiyonla aynı öğeleri, ancak iç içe bir yapı olmadan içerir.</span><span class="sxs-lookup"><span data-stu-id="d3312-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3312-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3312-105">Syntax</span></span>  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3312-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d3312-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="d3312-107">Tek bir koleksiyonda düzleştirmek için bir değer koleksiyonları koleksiyonu döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="d3312-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3312-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3312-108">Remarks</span></span>  
 <span data-ttu-id="d3312-109">`FLATTEN`, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="d3312-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="d3312-110">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d3312-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="d3312-111">@No__t-1 kümesi işleçleri için öncelik bilgisi [hariç](except-entity-sql.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d3312-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3312-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3312-112">Example</span></span>  
 <span data-ttu-id="d3312-113">Aşağıdaki Entity SQL sorgusu, bir koleksiyon koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürmek için `FLATTEN` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3312-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="d3312-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="d3312-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d3312-115">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="d3312-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d3312-116">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="d3312-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="d3312-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3312-117">See also</span></span>

- [<span data-ttu-id="d3312-118">Entity SQL başvurusu</span><span class="sxs-lookup"><span data-stu-id="d3312-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
