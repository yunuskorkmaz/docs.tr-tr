---
title: 'Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 94fbb681b20b9c920c20df2a9017f75a9aa9a6ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091528"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="2bbba-102">Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama</span><span class="sxs-lookup"><span data-stu-id="2bbba-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="2bbba-103">Aşağıdaki örnek, statik bölümleme gerçekleştiren PLINQ için basit bir özel bölümleyici uygulamak için bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="2bbba-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="2bbba-104">Bölümleyici dinamik bölümleri desteklemediği için, 'den <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>tüketilemez.</span><span class="sxs-lookup"><span data-stu-id="2bbba-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2bbba-105">Bu özel bölümleyici, her öğenin artan miktarda işlem süresi gerektirdiği veri kaynakları için varsayılan aralık bölümleyicisi üzerinden hız sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2bbba-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bbba-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2bbba-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="2bbba-107">Bu örnekteki bölümler, her öğe için işleme süresinde doğrusal bir artış varsayımına dayanır.</span><span class="sxs-lookup"><span data-stu-id="2bbba-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="2bbba-108">Gerçek dünyada, bu şekilde işlem sürelerini tahmin etmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="2bbba-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="2bbba-109">Belirli bir veri kaynağına sahip statik bir bölümleyici kullanıyorsanız, kaynak için bölümleme formülü optimize edebilir, yük dengeleme mantığı ekleyebilir veya [Dinamik Bölümleri Uygulama](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)' da gösterildiği gibi bir yığın bölümleme yaklaşımı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bbba-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbba-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bbba-110">See also</span></span>

- [<span data-ttu-id="2bbba-111">PLINQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="2bbba-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
