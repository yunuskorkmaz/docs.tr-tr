---
title: '&gt; (Büyük) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: b9cf4d5445060bbd013ae2d769c407e7f9ee9314
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="gt-greater-than-entity-sql"></a><span data-ttu-id="1f811-102">&gt; (Büyük) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="1f811-102">&gt; (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="1f811-103">Sol ifade sağ ifade büyük bir değere sahip olup olmadığını belirlemek için iki ifadeye karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="1f811-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f811-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f811-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f811-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f811-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1f811-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="1f811-106">Any valid expression.</span></span> <span data-ttu-id="1f811-107">Her iki ifadeleri örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f811-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1f811-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="1f811-108">Result Types</span></span>  
 <span data-ttu-id="1f811-109">`true` Sol ifade sağ ifade büyük bir değer varsa; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="1f811-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f811-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f811-110">Example</span></span>  
 <span data-ttu-id="1f811-111">Aşağıdaki varlık SQL sorgusu kullanır > karşılaştırma işlecinin sol ifade sağ ifade büyük bir değere sahip olup olmadığını belirlemek için iki ifadeye karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="1f811-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="1f811-112">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="1f811-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1f811-113">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1f811-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1f811-114">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1f811-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="1f811-115">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1f811-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="1f811-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f811-116">See Also</span></span>  
 [<span data-ttu-id="1f811-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1f811-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
