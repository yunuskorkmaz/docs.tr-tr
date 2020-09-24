---
title: < (küçüktür) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 389c50a697c90dadb075369fe696f7382caf3cff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161925"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="9676c-102">\< (Küçüktür) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9676c-102">\< (Less Than) (Entity SQL)</span></span>

<span data-ttu-id="9676c-103">Sol ifadenin doğru ifadeden daha küçük bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="9676c-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9676c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9676c-104">Syntax</span></span>  
  
```sql  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9676c-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="9676c-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="9676c-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="9676c-106">Any valid expression.</span></span> <span data-ttu-id="9676c-107">Her iki ifade örtülü olarak dönüştürülebilir veri türlerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9676c-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9676c-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="9676c-108">Result Types</span></span>  

 <span data-ttu-id="9676c-109">`true` sol ifade, doğru ifadeden daha küçük bir değere sahipse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="9676c-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9676c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9676c-110">Example</span></span>  

 <span data-ttu-id="9676c-111">Aşağıdaki Entity SQL sorgusu, sol deyimin doğru ifadeden küçük bir değere sahip olup olmadığını belirleyecek iki ifadeyi karşılaştırmak için < karşılaştırma işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9676c-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="9676c-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="9676c-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9676c-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9676c-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9676c-114">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="9676c-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9676c-115">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="9676c-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a><span data-ttu-id="9676c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9676c-116">See also</span></span>

- [<span data-ttu-id="9676c-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9676c-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
