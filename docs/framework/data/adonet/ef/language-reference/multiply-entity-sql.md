---
title: '* (Çarp) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 308df758d59a7e12a8b5a19ae72fcbee2f168490
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329732"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="19c4c-102">\* ((Varlık SQL) çarpın)</span><span class="sxs-lookup"><span data-stu-id="19c4c-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="19c4c-103">İki ifadeye çarpar.</span><span class="sxs-lookup"><span data-stu-id="19c4c-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19c4c-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="19c4c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="19c4c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="19c4c-106">Herhangi bir geçerli ifade herhangi birinin sayısal veri türleri.</span><span class="sxs-lookup"><span data-stu-id="19c4c-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="19c4c-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="19c4c-107">Result Types</span></span>  
 <span data-ttu-id="19c4c-108">Bu iki bağımsız değişken örtük tür yükseltme sonuçlarından veri türü.</span><span class="sxs-lookup"><span data-stu-id="19c4c-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="19c4c-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="19c4c-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19c4c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="19c4c-110">Example</span></span>  
 <span data-ttu-id="19c4c-111">Aşağıdaki varlık SQL sorgusu kullanır \* iki sayının çarpılacak aritmetik işleç.</span><span class="sxs-lookup"><span data-stu-id="19c4c-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="19c4c-112">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="19c4c-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="19c4c-113">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="19c4c-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="19c4c-114">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="19c4c-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="19c4c-115">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="19c4c-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="19c4c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19c4c-116">See also</span></span>

- [<span data-ttu-id="19c4c-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="19c4c-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
