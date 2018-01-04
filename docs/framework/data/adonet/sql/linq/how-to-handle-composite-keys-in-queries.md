---
title: "Nasıl yapılır: bileşik anahtarlar sorgularda işlemek"
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
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2b0954d4659d1cc39cead0658fbd21dcd6dd12e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="b4d21-102">Nasıl yapılır: bileşik anahtarlar sorgularda işlemek</span><span class="sxs-lookup"><span data-stu-id="b4d21-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="b4d21-103">Bazı işleçleri, tek bir bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="b4d21-103">Some operators can take only one argument.</span></span> <span data-ttu-id="b4d21-104">Bağımsız değişkeniniz veritabanından birden fazla sütunu içermelidir birleşimi temsil etmek için anonim bir tür oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4d21-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4d21-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4d21-105">Example</span></span>  
 <span data-ttu-id="b4d21-106">Aşağıdaki örnek, çağıran bir sorgu gösterir `GroupBy` tek sürebilir işleci `key` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b4d21-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="b4d21-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4d21-107">Example</span></span>  
 <span data-ttu-id="b4d21-108">Birleştirme, aşağıdaki örnekte olduğu gibi için de aynı durum geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="b4d21-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b4d21-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4d21-109">See Also</span></span>  
 [<span data-ttu-id="b4d21-110">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="b4d21-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
