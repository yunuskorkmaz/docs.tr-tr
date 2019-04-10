---
title: '- (Çıkart) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 2e4c08788ea57000e189c8371f0494641931184b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316693"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="a4e29-102">-(Çıkart) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="a4e29-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="a4e29-103">İki sayıyı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a4e29-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4e29-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a4e29-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a4e29-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a4e29-106">Herhangi bir geçerli ifade herhangi birinin sayısal veri türleri.</span><span class="sxs-lookup"><span data-stu-id="a4e29-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a4e29-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="a4e29-107">Result Types</span></span>  
 <span data-ttu-id="a4e29-108">Bu iki bağımsız değişken örtük tür yükseltme sonuçlarından veri türü.</span><span class="sxs-lookup"><span data-stu-id="a4e29-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="a4e29-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a4e29-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4e29-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4e29-110">Example</span></span>  
 <span data-ttu-id="a4e29-111">Aşağıdaki varlık SQL sorgusu kullanır aritmetik işleç iki sayının çıkarılacak.</span><span class="sxs-lookup"><span data-stu-id="a4e29-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="a4e29-112">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="a4e29-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a4e29-113">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="a4e29-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a4e29-114">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a4e29-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a4e29-115">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a4e29-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="a4e29-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4e29-116">See also</span></span>

- [<span data-ttu-id="a4e29-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a4e29-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
