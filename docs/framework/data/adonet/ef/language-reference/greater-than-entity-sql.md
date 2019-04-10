---
title: '> (Büyüktür) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: e1d13fa863eb79982d239f4e2dc298f7fcd1346f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328562"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="7f9c4-102">> (Büyüktür) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="7f9c4-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="7f9c4-103">Sol ifade sağ ifade daha büyük bir değere sahip olup olmadığını belirlemek için iki deyim karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="7f9c4-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f9c4-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f9c4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7f9c4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="7f9c4-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="7f9c4-106">Any valid expression.</span></span> <span data-ttu-id="7f9c4-107">Her iki ifade, örtük olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f9c4-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="7f9c4-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="7f9c4-108">Result Types</span></span>  
 `true` <span data-ttu-id="7f9c4-109">Sol ifade sağ ifade daha büyük bir değere sahipse; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="7f9c4-109">if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f9c4-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f9c4-110">Example</span></span>  
 <span data-ttu-id="7f9c4-111">Aşağıdaki varlık SQL sorgusu kullanır > sol ifade sağ ifade daha büyük bir değere sahip olup olmadığını belirlemek için iki deyim karşılaştırmak için kullanılan karşılaştırma işleci.</span><span class="sxs-lookup"><span data-stu-id="7f9c4-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="7f9c4-112">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="7f9c4-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7f9c4-113">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="7f9c4-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7f9c4-114">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7f9c4-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7f9c4-115">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7f9c4-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="7f9c4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f9c4-116">See also</span></span>

- [<span data-ttu-id="7f9c4-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7f9c4-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
