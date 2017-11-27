---
title: "Nasıl yapılır: Dinamik Bölümleri Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1e5dc93997918e0f7da29fa1f94c434a556f19f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="df85d-102">Nasıl yapılır: Dinamik Bölümleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="df85d-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="df85d-103">Aşağıdaki örnek, bir özel uygulamak gösterilmektedir <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> dinamik bölümleme uygular ve belirli aşırı kullanılan <xref:System.Threading.Tasks.Parallel.ForEach%2A> PLINQ gelen ve giden.</span><span class="sxs-lookup"><span data-stu-id="df85d-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df85d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="df85d-104">Example</span></span>  
 <span data-ttu-id="df85d-105">Bir bölüm çağırır her zaman <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralayıcı üzerinde Numaralandırıcı bölümü olan bir liste öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="df85d-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="df85d-106">PLINQ söz konusu olduğunda ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>, bölüm bir <xref:System.Threading.Tasks.Task> örneği.</span><span class="sxs-lookup"><span data-stu-id="df85d-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="df85d-107">İstekleri aynı anda birden çok iş parçacığı üzerinde gerçekleştiği olduğundan, geçerli dizin için erişim eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="df85d-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="df85d-108">Bu, her bir öbeğin bir öğe oluşan bölümleme öbek örneğidir.</span><span class="sxs-lookup"><span data-stu-id="df85d-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="df85d-109">Aynı anda daha fazla öğe sağlayarak kilit çakışması azaltın ve teorik olarak daha hızlı performans elde.</span><span class="sxs-lookup"><span data-stu-id="df85d-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="df85d-110">Ancak, tüm iş parçacıklarının tüm iş yapılana kadar meşgul tutmak için belirli bir noktada daha büyük öbek ek yük dengeleme mantık gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="df85d-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df85d-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df85d-111">See Also</span></span>  
 [<span data-ttu-id="df85d-112">PLINQ ve TPL için özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="df85d-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="df85d-113">Nasıl yapılır: statik bölümleme için bir Bölümleyici uygulama</span><span class="sxs-lookup"><span data-stu-id="df85d-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
