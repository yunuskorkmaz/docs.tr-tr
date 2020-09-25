---
title: KULLANMA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: bdab81ed8acae5e757de0a669922dc79d0303ee4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203598"
---
# <a name="using-entity-sql"></a><span data-ttu-id="2c3f4-102">KULLANMA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2c3f4-102">USING (Entity SQL)</span></span>

<span data-ttu-id="2c3f4-103">Sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c3f4-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c3f4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2c3f4-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="2c3f4-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2c3f4-105">Arguments</span></span>  

 `alias`  
 <span data-ttu-id="2c3f4-106">Bir ad alanını nitelemek için daha kısa bir diğer ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c3f4-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="2c3f4-107">Geçerli herhangi bir ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2c3f4-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c3f4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c3f4-108">Example</span></span>  

 <span data-ttu-id="2c3f4-109">Aşağıdaki Entity SQL sorgusu, bir sorgu ifadesinde kullanılan ad alanlarını belirtmek için USING işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c3f4-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="2c3f4-110">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2c3f4-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2c3f4-111">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2c3f4-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="2c3f4-112">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="2c3f4-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c3f4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c3f4-113">See also</span></span>

- [<span data-ttu-id="2c3f4-114">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="2c3f4-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="2c3f4-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2c3f4-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
