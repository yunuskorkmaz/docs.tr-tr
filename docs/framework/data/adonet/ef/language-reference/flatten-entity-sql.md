---
title: DÜZLEŞTİRME (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 76fba91f27479df19bbc4ac6e120d615a16f1d42
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115121"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="56ee6-102">DÜZLEŞTİRME (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="56ee6-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="56ee6-103">Değişkeninin bir koleksiyonlar koleksiyonu düzleştirilmiş bir koleksiyonuna dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="56ee6-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="56ee6-104">Yeni koleksiyon, hepsi aynı eski koleksiyonu, ancak iç içe bir yapı öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="56ee6-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ee6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56ee6-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="56ee6-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="56ee6-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="56ee6-107">Tek bir koleksiyona koleksiyonu düzleştirmek için değer koleksiyonları döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="56ee6-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56ee6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56ee6-108">Remarks</span></span>  
 `FLATTEN` <span data-ttu-id="56ee6-109">biri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56ee6-109">is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="56ee6-110">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="56ee6-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="56ee6-111">Bkz: [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56ee6-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ee6-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="56ee6-112">Example</span></span>  
 <span data-ttu-id="56ee6-113">Aşağıdaki varlık SQL sorgusu kullanır `FLATTEN` düzleştirilmiş bir koleksiyona değişkeninin bir koleksiyonlar koleksiyonu dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="56ee6-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="56ee6-114">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="56ee6-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="56ee6-115">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="56ee6-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="56ee6-116">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="56ee6-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="56ee6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56ee6-117">See also</span></span>

- [<span data-ttu-id="56ee6-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="56ee6-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
