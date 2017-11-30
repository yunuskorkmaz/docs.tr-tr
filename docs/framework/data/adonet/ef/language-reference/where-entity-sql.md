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
ms.openlocfilehash: 38d1b7e2b7662ef3b2fedbcce6ac23ce55a5468f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="where-entity-sql"></a><span data-ttu-id="4a853-102">Burada (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="4a853-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="4a853-103">WHERE yan tümcesi doğrudan sonra uygulanan [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4a853-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a853-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a853-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a853-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a853-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4a853-106">Bir Boolean türü.</span><span class="sxs-lookup"><span data-stu-id="4a853-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a853-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a853-107">Remarks</span></span>  
 <span data-ttu-id="4a853-108">WHERE yan tümcesi için açıklandığı gibi aynı semantiğine sahip [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4a853-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4a853-109">Bu koşul geçirmek için kaynak koleksiyonlarını öğelerini sınırlayarak sorgu ifadesi tarafından üretilen nesnelerin kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="4a853-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="4a853-110">İfade `e` Boolean türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a853-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="4a853-111">WHERE yan tümcesi FROM yan tümcesi hemen sonra ve hiçbir gruplandırma, sıralama veya yansıtma önce uygulandığı yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4a853-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="4a853-112">FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesi ifade için görünür durumdadır.</span><span class="sxs-lookup"><span data-stu-id="4a853-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a853-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a853-113">See Also</span></span>  
 [<span data-ttu-id="4a853-114">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4a853-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="4a853-115">Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="4a853-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
