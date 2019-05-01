---
title: 'Nasıl yapılır: Dinamik Bölümleri Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 792488e53ffb7f870e21fdd1ad3ef94bf0303b1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811559"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="0689f-102">Nasıl yapılır: Dinamik Bölümleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="0689f-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="0689f-103">Aşağıdaki örnek, özel bir uygulama gösterilmektedir <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> dinamik bölümlemeyi uygular ve belirli bir aşırı kullanılan <xref:System.Threading.Tasks.Parallel.ForEach%2A> ve PLINQ.</span><span class="sxs-lookup"><span data-stu-id="0689f-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0689f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0689f-104">Example</span></span>  
 <span data-ttu-id="0689f-105">Bir bölüm çağırdığında <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralandırıcıda Numaralandırıcı bölüm bir liste öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0689f-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="0689f-106">PLINQ söz konusu olduğunda ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>, bölüm bir <xref:System.Threading.Tasks.Task> örneği.</span><span class="sxs-lookup"><span data-stu-id="0689f-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="0689f-107">Geçerli dizin için erişim isteklerini aynı anda birden çok iş parçacığında olmuyor çünkü eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="0689f-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="0689f-108">Bu, her bir öbeği oluşan bir öğe bölümleme öbek örneğidir.</span><span class="sxs-lookup"><span data-stu-id="0689f-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="0689f-109">Aynı anda daha fazla öğe sağlayarak üzerinde kilit çekişmeyi azaltmak ve teorik olarak daha hızlı performans elde.</span><span class="sxs-lookup"><span data-stu-id="0689f-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="0689f-110">Ancak, tüm iş tamamlanana kadar tüm iş parçacıklarının meşgul tutmak için belirli bir noktada daha büyük öbekler Yük Dengeleme ilave bir mantık gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="0689f-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0689f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0689f-111">See also</span></span>

- [<span data-ttu-id="0689f-112">PLINQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="0689f-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="0689f-113">Nasıl yapılır: Statik bölümleme için bir Bölümleyici uygulama</span><span class="sxs-lookup"><span data-stu-id="0689f-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
