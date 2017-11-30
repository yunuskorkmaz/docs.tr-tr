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
ms.openlocfilehash: 226f7fa14331ee8e2500ac91a665e86928e37f8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="dc433-102">(Varlık SQL) DÜZLEŞTİRME</span><span class="sxs-lookup"><span data-stu-id="dc433-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="dc433-103">Değişkeninin bir koleksiyonlar koleksiyonu düzleştirilmiş bir koleksiyonuna dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="dc433-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="dc433-104">Yeni koleksiyon öğeleri eski koleksiyonu, ancak iç içe geçmiş yapısı olmadan aynı içerir.</span><span class="sxs-lookup"><span data-stu-id="dc433-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc433-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc433-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="dc433-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="dc433-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="dc433-107">Tek bir koleksiyona düzleştirmek için değer koleksiyonları koleksiyonu döndüren herhangi geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="dc433-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc433-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc433-108">Remarks</span></span>  
 <span data-ttu-id="dc433-109">`FLATTEN`biri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dc433-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="dc433-110">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="dc433-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="dc433-111">Bkz: [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) için öncelik bilgi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dc433-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc433-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc433-112">Example</span></span>  
 <span data-ttu-id="dc433-113">Aşağıdaki varlık SQL sorgusu kullanır `FLATTEN` değişkeninin bir koleksiyonlar koleksiyonu düzleştirilmiş bir koleksiyona dönüştürmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="dc433-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="dc433-114">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="dc433-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="dc433-115">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="dc433-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="dc433-116">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="dc433-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="dc433-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc433-117">See Also</span></span>  
 [<span data-ttu-id="dc433-118">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="dc433-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
