---
title: Sabit ifadeleri
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 328284ce07a0361dbfd25b0d765000b497156ff7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="constant-expressions"></a><span data-ttu-id="ee101-102">Sabit ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ee101-102">Constant Expressions</span></span>
<span data-ttu-id="ee101-103">Sabit bir ifade sabit bir değer oluşur.</span><span class="sxs-lookup"><span data-stu-id="ee101-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="ee101-104">Sabit değerler doğrudan istemcide çeviri içermeyen sabit komut ağacı ifadeleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ee101-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="ee101-105">Bu, sabit bir değer neden ifadeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ee101-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="ee101-106">Bu nedenle, veri kaynağı davranışı sabitleri içeren tüm ifadeler için beklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ee101-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="ee101-107">Bu CLR davranışından farklıdır davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee101-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="ee101-108">Aşağıdaki örnek, sunucu üzerinde değerlendirilir sabit bir ifade gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee101-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="ee101-109">bir kullanıcı sınıfı bir sabit değer olarak kullanılmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ee101-109"> does not support using a user class as a constant.</span></span> <span data-ttu-id="ee101-110">Ancak, bir özellik referansı bir kullanıcı sınıfını bir sabit olarak kabul edilir ve komut ağacı sabit bir ifade için dönüştürülür ve veri kaynağı üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ee101-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee101-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee101-111">See Also</span></span>  
 [<span data-ttu-id="ee101-112">LINQ to Entities Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="ee101-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
