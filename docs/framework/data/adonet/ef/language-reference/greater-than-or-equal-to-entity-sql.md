---
title: '>= (Büyüktür veya eşittir) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: fb97786687616ff92f0e4402c86aef02de2e70c9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250878"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="2b6e3-102">> = (büyüktür veya eşittir) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2b6e3-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="2b6e3-103">Sol ifadenin sağ ifadeden büyük veya ona eşit bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="2b6e3-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b6e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b6e3-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b6e3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2b6e3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2b6e3-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="2b6e3-106">Any valid expression.</span></span> <span data-ttu-id="2b6e3-107">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b6e3-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2b6e3-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="2b6e3-108">Result Types</span></span>  
 <span data-ttu-id="2b6e3-109">`true`Sol ifadede sağ ifadeden daha büyük veya ona eşit bir değer varsa; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="2b6e3-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b6e3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b6e3-110">Example</span></span>  
 <span data-ttu-id="2b6e3-111">Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeden büyük veya ona eşit bir değere sahip olup olmadığını belirleyecek iki ifadeyi karşılaştırmak için > = karşılaştırma işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b6e3-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="2b6e3-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2b6e3-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2b6e3-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2b6e3-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2b6e3-114">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="2b6e3-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2b6e3-115">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="2b6e3-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="2b6e3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b6e3-116">See also</span></span>

- [<span data-ttu-id="2b6e3-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2b6e3-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
