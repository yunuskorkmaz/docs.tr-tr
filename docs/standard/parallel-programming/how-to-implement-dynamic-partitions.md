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
ms.openlocfilehash: 3970566b4e3f51ce538c328d4e69b20ec22ec09b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091417"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="f7ae2-102">Nasıl yapılır: Dinamik Bölümleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="f7ae2-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="f7ae2-103">Aşağıdaki örnek, dinamik bölümlendirme uygulayan özel bir <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> nasıl uygulanacağını gösterir ve PLıNQ 'ten <xref:System.Threading.Tasks.Parallel.ForEach%2A> belirli aşırı yüklerden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7ae2-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7ae2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7ae2-104">Example</span></span>

<span data-ttu-id="f7ae2-105">Numaralandırıcı üzerinde <xref:System.Collections.IEnumerator.MoveNext%2A> bir bölüm çağırdığında, Numaralandırıcı bölüm bir liste öğesiyle birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7ae2-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="f7ae2-106">PLıNQ ve <xref:System.Threading.Tasks.Parallel.ForEach%2A>söz konusu olduğunda, bölüm bir <xref:System.Threading.Tasks.Task> örneğidir.</span><span class="sxs-lookup"><span data-stu-id="f7ae2-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="f7ae2-107">İstekler birden çok iş parçacığında eşzamanlı olarak yapıldığından, geçerli dizine erişim eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="f7ae2-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="f7ae2-108">Bu, öbek bölümlendirme bir örneğidir ve her bir öbek bir öğeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f7ae2-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="f7ae2-109">Tek seferde daha fazla öğe sağlayarak kilit üzerindeki çekişmeyi azaltabilir ve teorik olarak daha hızlı performans elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ae2-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="f7ae2-110">Ancak, bazı bir noktada, tüm işler tamamlanana kadar tüm iş parçacıklarını meşgul tutmak için daha büyük parçalar ek yük dengeleme mantığını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="f7ae2-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ae2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7ae2-111">See also</span></span>

* [<span data-ttu-id="f7ae2-112">PLINQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="f7ae2-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="f7ae2-113">Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama</span><span class="sxs-lookup"><span data-stu-id="f7ae2-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
