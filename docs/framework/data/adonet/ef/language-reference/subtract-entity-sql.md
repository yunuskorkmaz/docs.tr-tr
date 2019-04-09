---
title: '- (Çıkart) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: d7eee2fdb8e61711b453f4f444cc8dc8d5a43558
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128836"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="970f9-102">-(Çıkart) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="970f9-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="970f9-103">İki sayıyı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="970f9-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="970f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="970f9-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="970f9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="970f9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="970f9-106">Herhangi bir geçerli ifade herhangi birinin sayısal veri türleri.</span><span class="sxs-lookup"><span data-stu-id="970f9-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="970f9-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="970f9-107">Result Types</span></span>  
 <span data-ttu-id="970f9-108">Bu iki bağımsız değişken örtük tür yükseltme sonuçlarından veri türü.</span><span class="sxs-lookup"><span data-stu-id="970f9-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="970f9-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="970f9-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="970f9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="970f9-110">Example</span></span>  
 <span data-ttu-id="970f9-111">Aşağıdaki varlık SQL sorgusu kullanır aritmetik işleç iki sayının çıkarılacak.</span><span class="sxs-lookup"><span data-stu-id="970f9-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="970f9-112">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="970f9-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="970f9-113">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="970f9-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="970f9-114">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="970f9-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="970f9-115">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="970f9-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="970f9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="970f9-116">See also</span></span>

- [<span data-ttu-id="970f9-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="970f9-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
