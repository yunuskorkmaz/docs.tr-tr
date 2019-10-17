---
title: Modül (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 4bbdbe53403cfec2568cfac320fc7ab1ad2725b0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319596"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="dfee1-102">Modül (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dfee1-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="dfee1-103">Bir ifadenin kalan kısmını başka bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="dfee1-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfee1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfee1-104">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="dfee1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dfee1-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="dfee1-106">Bölünecek sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="dfee1-106">The numeric expression to divide.</span></span> <span data-ttu-id="dfee1-107">`dividend`, herhangi bir sayısal veri türü için geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="dfee1-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="dfee1-108">Bölüneni bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="dfee1-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="dfee1-109">`divisor`, herhangi bir sayısal veri türü için geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="dfee1-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="dfee1-110">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="dfee1-110">Result Types</span></span>  
 <span data-ttu-id="dfee1-111">EDM. Int32</span><span class="sxs-lookup"><span data-stu-id="dfee1-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfee1-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfee1-112">Example</span></span>  
 <span data-ttu-id="dfee1-113">Aşağıdaki Entity SQL sorgusu, bir ifadenin kalan kısmını başka bir ifade döndürmek için% aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dfee1-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="dfee1-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="dfee1-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dfee1-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="dfee1-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="dfee1-116">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="dfee1-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="dfee1-117">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="dfee1-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="dfee1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfee1-118">See also</span></span>

- [<span data-ttu-id="dfee1-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="dfee1-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
