---
title: '&lt; (Küçüktür) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 0c2185f824cfbe201b4138d0082e3edcf93e6a7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598322"
---
# <a name="lt-less-than-entity-sql"></a><span data-ttu-id="2ac2b-102">&lt; (Küçüktür) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="2ac2b-102">&lt; (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="2ac2b-103">Sol ifade sağ ifade'den küçük bir değere sahip olup olmadığını belirlemek için iki deyim karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="2ac2b-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ac2b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ac2b-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2ac2b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2ac2b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2ac2b-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="2ac2b-106">Any valid expression.</span></span> <span data-ttu-id="2ac2b-107">Her iki ifade, örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ac2b-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2ac2b-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="2ac2b-108">Result Types</span></span>  
 <span data-ttu-id="2ac2b-109">`true` Sol ifade sağ ifade'den küçük bir değere sahipse; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="2ac2b-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ac2b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ac2b-110">Example</span></span>  
 <span data-ttu-id="2ac2b-111">Aşağıdaki varlık SQL sorgusu kullanır < sol ifade sağ ifade'den küçük bir değere sahip olup olmadığını belirlemek için iki deyim karşılaştırmak için kullanılan karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="2ac2b-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="2ac2b-112">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="2ac2b-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2ac2b-113">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2ac2b-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="2ac2b-114">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2ac2b-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="2ac2b-115">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="2ac2b-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="2ac2b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ac2b-116">See also</span></span>
- [<span data-ttu-id="2ac2b-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2ac2b-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
