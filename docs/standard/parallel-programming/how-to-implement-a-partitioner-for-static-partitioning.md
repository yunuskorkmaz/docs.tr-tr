---
title: 'Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 22d2cf788d4726488512703356a75f84efd04250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278512"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="79a36-102">Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama</span><span class="sxs-lookup"><span data-stu-id="79a36-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="79a36-103">Aşağıdaki örnek, statik bölümlendirme gerçekleştiren PLıNQ için basit bir özel bölümleyici uygulamak için bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="79a36-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="79a36-104">Bölümleyici dinamik bölümleri desteklemediğinden, bu, ' den tüketilemez değildir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="79a36-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="79a36-105">Bu belirli bir bölümleyici, her öğenin artan miktarda işleme süresi gerektirdiği veri kaynakları için varsayılan Aralık bölümleyici 'nin üzerinde iyileşme sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="79a36-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79a36-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="79a36-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="79a36-107">Bu örnekteki bölümler her öğe için işleme zamanında doğrusal bir artışın varsayımına dayanır.</span><span class="sxs-lookup"><span data-stu-id="79a36-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="79a36-108">Gerçek dünyada, işleme sürelerini bu şekilde tahmin etmek zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="79a36-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="79a36-109">Belirli bir veri kaynağıyla statik bir bölümleyici kullanıyorsanız, kaynağın bölümlendirme formülünü iyileştirebilir, Yük Dengeleme mantığını ekleyebilir veya [nasıl yapılır: dinamik bölümleri uygulama](how-to-implement-dynamic-partitions.md)bölümünde gösterildiği gibi öbek bölümleme yaklaşımını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79a36-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a36-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79a36-110">See also</span></span>

- [<span data-ttu-id="79a36-111">PLıNQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="79a36-111">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
