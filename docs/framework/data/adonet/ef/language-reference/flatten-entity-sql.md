---
title: "(Varlık SQL) DÜZLEŞTİRME"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 467277a1697f9f6ca4da7278045cbec34202eed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="6d223-102">(Varlık SQL) DÜZLEŞTİRME</span><span class="sxs-lookup"><span data-stu-id="6d223-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="6d223-103">Değişkeninin bir koleksiyonlar koleksiyonu düzleştirilmiş bir koleksiyonuna dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6d223-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="6d223-104">Yeni koleksiyon öğeleri eski koleksiyonu, ancak iç içe geçmiş yapısı olmadan aynı içerir.</span><span class="sxs-lookup"><span data-stu-id="6d223-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d223-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d223-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="6d223-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="6d223-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="6d223-107">Tek bir koleksiyona düzleştirmek için değer koleksiyonları koleksiyonu döndüren herhangi geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="6d223-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d223-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d223-108">Remarks</span></span>  
 <span data-ttu-id="6d223-109">`FLATTEN`biri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6d223-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="6d223-110">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6d223-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="6d223-111">Bkz: [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) için öncelik bilgi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6d223-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d223-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d223-112">Example</span></span>  
 <span data-ttu-id="6d223-113">Aşağıdaki varlık SQL sorgusu kullanır `FLATTEN` değişkeninin bir koleksiyonlar koleksiyonu düzleştirilmiş bir koleksiyona dönüştürmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="6d223-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="6d223-114">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="6d223-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6d223-115">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6d223-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6d223-116">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="6d223-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="6d223-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d223-117">See Also</span></span>  
 [<span data-ttu-id="6d223-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6d223-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
