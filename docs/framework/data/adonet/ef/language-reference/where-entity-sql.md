---
title: "Burada (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2ad170500770bc370eb67a04ab29d0c9f9dcaabd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="where-entity-sql"></a><span data-ttu-id="7f681-102">Burada (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="7f681-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="7f681-103">WHERE yan tümcesi doğrudan sonra uygulanan [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="7f681-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f681-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f681-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f681-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7f681-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="7f681-106">Bir Boolean türü.</span><span class="sxs-lookup"><span data-stu-id="7f681-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f681-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f681-107">Remarks</span></span>  
 <span data-ttu-id="7f681-108">WHERE yan tümcesi için açıklandığı gibi aynı semantiğine sahip [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f681-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7f681-109">Bu koşul geçirmek için kaynak koleksiyonlarını öğelerini sınırlayarak sorgu ifadesi tarafından üretilen nesnelerin kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="7f681-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="7f681-110">İfade `e` Boolean türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f681-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="7f681-111">WHERE yan tümcesi FROM yan tümcesi hemen sonra ve hiçbir gruplandırma, sıralama veya yansıtma önce uygulandığı yerini alır.</span><span class="sxs-lookup"><span data-stu-id="7f681-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="7f681-112">FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesi ifade için görünür durumdadır.</span><span class="sxs-lookup"><span data-stu-id="7f681-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f681-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7f681-113">See Also</span></span>  
 [<span data-ttu-id="7f681-114">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7f681-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="7f681-115">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7f681-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
