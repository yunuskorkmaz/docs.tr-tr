---
description: 'Hakkında daha fazla bilgi edinin: USING (Entity SQL)'
title: KULLANMA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 084ab56f25041377dd6a0a35dd743122f482eeba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795059"
---
# <a name="using-entity-sql"></a><span data-ttu-id="7ce12-103">KULLANMA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7ce12-103">USING (Entity SQL)</span></span>

<span data-ttu-id="7ce12-104">Sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ce12-104">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ce12-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7ce12-105">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="7ce12-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="7ce12-106">Arguments</span></span>  

 `alias`  
 <span data-ttu-id="7ce12-107">Bir ad alanını nitelemek için daha kısa bir diğer ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ce12-107">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="7ce12-108">Geçerli herhangi bir ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7ce12-108">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ce12-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ce12-109">Example</span></span>  

 <span data-ttu-id="7ce12-110">Aşağıdaki Entity SQL sorgusu, bir sorgu ifadesinde kullanılan ad alanlarını belirtmek için USING işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ce12-110">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="7ce12-111">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="7ce12-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7ce12-112">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="7ce12-112">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="7ce12-113">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="7ce12-113">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ce12-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ce12-114">See also</span></span>

- [<span data-ttu-id="7ce12-115">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="7ce12-115">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="7ce12-116">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7ce12-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
