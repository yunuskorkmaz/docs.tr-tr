---
title: "Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 125bef8d43e16c120e88250a4d9d5a4ff3f63dba
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="21e5a-102">Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama</span><span class="sxs-lookup"><span data-stu-id="21e5a-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="21e5a-103">Aşağıdaki örnek, statik bölümleme gerçekleştirir PLINQ için basit bir özel bölümleyici uygulamak için bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="21e5a-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="21e5a-104">Bölümleyici dinamik bölümleri desteklemiyor, gelen tüketilebilir değildir, çünkü <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21e5a-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="21e5a-105">Bu belirli bölümleyici speedup her öğe bir artan süreyi işleme gerektiren veri kaynakları için varsayılan aralığı bölümleyici sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="21e5a-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21e5a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="21e5a-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="21e5a-107">Bu örnekte bölümleri her öğe için işleme süresi doğrusal bir artış varsayımına dayanır.</span><span class="sxs-lookup"><span data-stu-id="21e5a-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="21e5a-108">Gerçek Hayatta, bu şekilde işleme sürelerini tahmin etmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="21e5a-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="21e5a-109">Statik bölümleyici belirli veri kaynağı ile kullanıyorsanız, bölümleme formülü kaynağı için en iyi duruma getirme, Yük Dengeleme mantığı ekleyebilir veya yaklaşım şekilde bölümleme bir öbek kullanmak [nasıl yapılır: dinamik bölümleri uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="21e5a-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e5a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21e5a-110">See Also</span></span>  
 [<span data-ttu-id="21e5a-111">PLINQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="21e5a-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
