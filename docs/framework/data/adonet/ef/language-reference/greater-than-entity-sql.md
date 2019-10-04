---
title: '> (Büyüktür) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: f2d3a0ed81cf75b7e567dbd07e119629ea47ac69
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833767"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="aad7d-102">> (Büyüktür) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="aad7d-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="aad7d-103">Sol ifadenin sağ ifadeden daha büyük bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="aad7d-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aad7d-104">Syntax</span></span>  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="aad7d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="aad7d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="aad7d-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="aad7d-106">Any valid expression.</span></span> <span data-ttu-id="aad7d-107">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aad7d-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="aad7d-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="aad7d-108">Result Types</span></span>  
 <span data-ttu-id="aad7d-109">sol ifade sağ ifadeden daha büyük bir değere sahipse, `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="aad7d-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aad7d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="aad7d-110">Example</span></span>  
 <span data-ttu-id="aad7d-111">Aşağıdaki Entity SQL sorgusu, sol ifadenin sağ ifadeden daha büyük bir değere sahip olup olmadığını belirleyecek iki ifadeyi karşılaştırmak için > karşılaştırma işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="aad7d-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="aad7d-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="aad7d-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="aad7d-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="aad7d-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="aad7d-114">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="aad7d-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="aad7d-115">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="aad7d-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="aad7d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aad7d-116">See also</span></span>

- [<span data-ttu-id="aad7d-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="aad7d-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
