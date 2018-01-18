---
title: "Bir tür için genel bir IEnumerable Dönüştür"
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
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fa15e1336c31aec47fb2255f224146b9ac7e429d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="d73f1-102">Bir tür için genel bir IEnumerable Dönüştür</span><span class="sxs-lookup"><span data-stu-id="d73f1-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="d73f1-103">Kullanım <xref:System.Linq.Enumerable.AsEnumerable%2A> genel yazılan bağımsız değişkenini döndürmesine izin `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="d73f1-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d73f1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d73f1-104">Example</span></span>  
 <span data-ttu-id="d73f1-105">Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (genel varsayılan kullanarak `Query`) SQL sorgu dönüştürmek ve sunucuda yürütmek isteriz.</span><span class="sxs-lookup"><span data-stu-id="d73f1-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="d73f1-106">Ancak `where` yan tümcesinde başvuruda bulunan bir kullanıcı tarafından tanımlanan istemci-tarafı yöntemi (`isValidProduct`), hangi dönüştürülemiyor SQL.</span><span class="sxs-lookup"><span data-stu-id="d73f1-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="d73f1-107">İstemci-tarafı genel belirtmek için çözümdür <xref:System.Collections.Generic.IEnumerable%601> uyarlamasını `where` genel değiştirmek için <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="d73f1-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="d73f1-108">Harekete geçirerek bunu <xref:System.Linq.Enumerable.AsEnumerable%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="d73f1-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="d73f1-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d73f1-109">See Also</span></span>  
 [<span data-ttu-id="d73f1-110">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="d73f1-110">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
