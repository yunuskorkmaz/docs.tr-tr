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
ms.openlocfilehash: 168e721eee7f5253412438a2185934f01bf081c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="8e9e8-102">Nasıl yapılır: bileşik anahtarlar sorgularda işlemek</span><span class="sxs-lookup"><span data-stu-id="8e9e8-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="8e9e8-103">Bazı işleçleri, tek bir bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="8e9e8-103">Some operators can take only one argument.</span></span> <span data-ttu-id="8e9e8-104">Bağımsız değişkeniniz veritabanından birden fazla sütunu içermelidir birleşimi temsil etmek için anonim bir tür oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e9e8-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e9e8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e9e8-105">Example</span></span>  
 <span data-ttu-id="8e9e8-106">Aşağıdaki örnek, çağıran bir sorgu gösterir `GroupBy` tek sürebilir işleci `key` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="8e9e8-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="8e9e8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e9e8-107">Example</span></span>  
 <span data-ttu-id="8e9e8-108">Birleştirme, aşağıdaki örnekte olduğu gibi için de aynı durum geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="8e9e8-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8e9e8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e9e8-109">See Also</span></span>  
 [<span data-ttu-id="8e9e8-110">Sorgu kavramları</span><span class="sxs-lookup"><span data-stu-id="8e9e8-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
