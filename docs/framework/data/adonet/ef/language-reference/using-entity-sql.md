---
title: KULLANMA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 0bcd4a2140a04fa0ecbfa7eee450ed029f278286
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319212"
---
# <a name="using-entity-sql"></a><span data-ttu-id="f37a5-102">KULLANMA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f37a5-102">USING (Entity SQL)</span></span>
<span data-ttu-id="f37a5-103">Sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f37a5-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f37a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f37a5-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="f37a5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f37a5-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="f37a5-106">Bir ad alanını nitelemek için daha kısa bir diğer ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="f37a5-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="f37a5-107">Geçerli herhangi bir ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f37a5-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f37a5-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f37a5-108">Example</span></span>  
 <span data-ttu-id="f37a5-109">Aşağıdaki Entity SQL sorgusu, bir sorgu ifadesinde kullanılan ad alanlarını belirtmek için USING işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f37a5-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="f37a5-110">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="f37a5-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f37a5-111">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="f37a5-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="f37a5-112">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="f37a5-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="f37a5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f37a5-113">See also</span></span>

- [<span data-ttu-id="f37a5-114">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="f37a5-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="f37a5-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f37a5-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
