---
title: "(Varlık SQL) kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cc69dba9e70bb6bcc870b1cb92e98cb656cad98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-entity-sql"></a><span data-ttu-id="49181-102">(Varlık SQL) kullanma</span><span class="sxs-lookup"><span data-stu-id="49181-102">USING (Entity SQL)</span></span>
<span data-ttu-id="49181-103">Ad alanları sorgu ifadesinde kullanılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="49181-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49181-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49181-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="49181-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="49181-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="49181-106">Bir ad alanıyla nitelemek için daha kısa bir diğer ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="49181-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="49181-107">Tüm geçerli ad alanı.</span><span class="sxs-lookup"><span data-stu-id="49181-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49181-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="49181-108">Example</span></span>  
 <span data-ttu-id="49181-109">Aşağıdaki varlık SQL sorgusunu kullanarak işleci sorgu ifadesinde kullanılan ad alanları belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="49181-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="49181-110">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="49181-110">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="49181-111">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="49181-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="49181-112">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="49181-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="49181-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="49181-113">See Also</span></span>  
 [<span data-ttu-id="49181-114">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="49181-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [<span data-ttu-id="49181-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="49181-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
