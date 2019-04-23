---
title: DÜZLEŞTİRME (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 4f9a6315fc9cc2f295c21cc5fb7e1007e47796b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304583"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="64e9c-102">DÜZLEŞTİRME (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="64e9c-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="64e9c-103">Değişkeninin bir koleksiyonlar koleksiyonu düzleştirilmiş bir koleksiyonuna dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="64e9c-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="64e9c-104">Yeni koleksiyon, hepsi aynı eski koleksiyonu, ancak iç içe bir yapı öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="64e9c-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64e9c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64e9c-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="64e9c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="64e9c-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="64e9c-107">Tek bir koleksiyona koleksiyonu düzleştirmek için değer koleksiyonları döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="64e9c-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64e9c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64e9c-108">Remarks</span></span>  
 <span data-ttu-id="64e9c-109">`FLATTEN` biri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64e9c-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="64e9c-110">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="64e9c-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="64e9c-111">Bkz: [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64e9c-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64e9c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="64e9c-112">Example</span></span>  
 <span data-ttu-id="64e9c-113">Aşağıdaki varlık SQL sorgusu kullanır `FLATTEN` düzleştirilmiş bir koleksiyona değişkeninin bir koleksiyonlar koleksiyonu dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="64e9c-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="64e9c-114">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="64e9c-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="64e9c-115">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="64e9c-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="64e9c-116">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="64e9c-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="64e9c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64e9c-117">See also</span></span>

- [<span data-ttu-id="64e9c-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="64e9c-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
