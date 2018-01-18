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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 11687b1218c61acde7a68bb8fc112e287e5e1c38
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="where-entity-sql"></a><span data-ttu-id="30c22-102">Burada (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="30c22-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="30c22-103">WHERE yan tümcesi doğrudan sonra uygulanan [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="30c22-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30c22-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="30c22-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="30c22-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="30c22-106">Bir Boolean türü.</span><span class="sxs-lookup"><span data-stu-id="30c22-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30c22-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30c22-107">Remarks</span></span>  
 <span data-ttu-id="30c22-108">WHERE yan tümcesi için açıklandığı gibi aynı semantiğine sahip [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="30c22-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="30c22-109">Bu koşul geçirmek için kaynak koleksiyonlarını öğelerini sınırlayarak sorgu ifadesi tarafından üretilen nesnelerin kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="30c22-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="30c22-110">İfade `e` Boolean türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30c22-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="30c22-111">WHERE yan tümcesi FROM yan tümcesi hemen sonra ve hiçbir gruplandırma, sıralama veya yansıtma önce uygulandığı yerini alır.</span><span class="sxs-lookup"><span data-stu-id="30c22-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="30c22-112">FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesi ifade için görünür durumdadır.</span><span class="sxs-lookup"><span data-stu-id="30c22-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c22-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30c22-113">See Also</span></span>  
 [<span data-ttu-id="30c22-114">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="30c22-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="30c22-115">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="30c22-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
