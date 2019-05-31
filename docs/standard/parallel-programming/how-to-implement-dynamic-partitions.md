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
ms.openlocfilehash: 5719c6afc1c5efc6138f0a4931d1725a6f20909a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424040"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="94f9d-102">Nasıl yapılır: Dinamik Bölümleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="94f9d-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="94f9d-103">Aşağıdaki örnek, özel bir uygulama gösterilmektedir <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> dinamik bölümlemeyi uygular ve belirli bir aşırı kullanılan <xref:System.Threading.Tasks.Parallel.ForEach%2A> ve PLINQ.</span><span class="sxs-lookup"><span data-stu-id="94f9d-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94f9d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="94f9d-104">Example</span></span>

<span data-ttu-id="94f9d-105">Bir bölüm çağırdığında <xref:System.Collections.IEnumerator.MoveNext%2A> Numaralandırıcıda Numaralandırıcı bölüm bir liste öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="94f9d-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="94f9d-106">PLINQ söz konusu olduğunda ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>, bölüm bir <xref:System.Threading.Tasks.Task> örneği.</span><span class="sxs-lookup"><span data-stu-id="94f9d-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="94f9d-107">Geçerli dizin için erişim isteklerini aynı anda birden çok iş parçacığında olmuyor çünkü eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="94f9d-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="94f9d-108">Bu, her bir öbeği oluşan bir öğe bölümleme öbek örneğidir.</span><span class="sxs-lookup"><span data-stu-id="94f9d-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="94f9d-109">Aynı anda daha fazla öğe sağlayarak üzerinde kilit çekişmeyi azaltmak ve teorik olarak daha hızlı performans elde.</span><span class="sxs-lookup"><span data-stu-id="94f9d-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="94f9d-110">Ancak, tüm iş tamamlanana kadar tüm iş parçacıklarının meşgul tutmak için belirli bir noktada daha büyük öbekler Yük Dengeleme ilave bir mantık gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="94f9d-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f9d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94f9d-111">See also</span></span>

* [<span data-ttu-id="94f9d-112">PLINQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="94f9d-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="94f9d-113">Nasıl yapılır: Statik bölümleme için bir Bölümleyici uygulama</span><span class="sxs-lookup"><span data-stu-id="94f9d-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
