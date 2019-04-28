---
title: 'Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 302d7d98d04e528d205edf38c3fa13bb3f2b2252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638265"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="4fd68-102">Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama</span><span class="sxs-lookup"><span data-stu-id="4fd68-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="4fd68-103">Aşağıdaki örnek, statik bölümleme gerçekleştiren PLINQ için basit ve özel bir bölümleyici uygulama yollarından biri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4fd68-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="4fd68-104">Dinamik bölümleri bölümleyici desteklemez, gelen tüketilebilir değildir, çünkü <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4fd68-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4fd68-105">Bu özel bölümleyici, artan bir işleme zaman miktarı gerektiren her öğe için veri kaynakları için varsayılan aralık bölümleyici hızlandırmayı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4fd68-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fd68-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4fd68-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="4fd68-107">Bu örnekte bölümleri işleme süresinde her öğe için doğrusal bir artışı varsayımına dayanır.</span><span class="sxs-lookup"><span data-stu-id="4fd68-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="4fd68-108">Gerçek dünyada, işlem süreleri bu şekilde tahmin etmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fd68-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="4fd68-109">Statik bölümleyici belirli veri kaynağı ile kullanıyorsanız, bölümleme formülü kaynağı için en iyi duruma getirme, Yük Dengeleme mantığı ekleyebilir veya bir öbek yaklaşım gösterildiği şekilde bölümleme kullanın [nasıl yapılır: Dinamik bölümleri uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="4fd68-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd68-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fd68-110">See also</span></span>

- [<span data-ttu-id="4fd68-111">PLINQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="4fd68-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
