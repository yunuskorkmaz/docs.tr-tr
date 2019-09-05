---
title: = (Eşittir) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: ec87ec682e1773c001c225567a35b3cedc9c5aba
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251001"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="b30e3-102">= (Eşittir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b30e3-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="b30e3-103">İki ifadenin eşitliğini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="b30e3-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b30e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b30e3-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b30e3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b30e3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b30e3-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="b30e3-106">Any valid expression.</span></span> <span data-ttu-id="b30e3-107">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b30e3-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b30e3-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="b30e3-108">Result Types</span></span>  
 <span data-ttu-id="b30e3-109">`true`sol ifade sağ ifadeye eşitse; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="b30e3-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b30e3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b30e3-110">Remarks</span></span>  
 <span data-ttu-id="b30e3-111">= = İşleci = = ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b30e3-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b30e3-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b30e3-112">Example</span></span>  
 <span data-ttu-id="b30e3-113">Aşağıdaki Entity SQL sorgusu iki ifadenin eşitliğini karşılaştırmak için = Comparison işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b30e3-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="b30e3-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b30e3-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b30e3-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b30e3-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b30e3-116">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="b30e3-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b30e3-117">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="b30e3-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="b30e3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b30e3-118">See also</span></span>

- [<span data-ttu-id="b30e3-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b30e3-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
