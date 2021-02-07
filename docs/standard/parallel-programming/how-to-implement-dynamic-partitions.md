---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: dinamik bölümleri uygulama'
title: 'Nasıl yapılır: Dinamik Bölümleri Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 3f0b383b9f4f7a47acb21d3ec3451b1761a3368c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701969"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="3a561-103">Nasıl yapılır: Dinamik Bölümleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="3a561-103">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="3a561-104">Aşağıdaki örnek, dinamik bölümlendirme uygulayan bir özel nasıl uygulanacağını <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> ve belirli aşırı yüklerden <xref:System.Threading.Tasks.Parallel.ForEach%2A> ve PLINQ 'ten nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a561-104">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a561-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a561-105">Example</span></span>

<span data-ttu-id="3a561-106">Numaralandırıcı üzerinde bir bölüm çağırdığında <xref:System.Collections.IEnumerator.MoveNext%2A> , Numaralandırıcı bölüm bir liste öğesiyle birlikte sunulur.</span><span class="sxs-lookup"><span data-stu-id="3a561-106">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="3a561-107">PLıNQ ve durumunda <xref:System.Threading.Tasks.Parallel.ForEach%2A> , bölüm bir <xref:System.Threading.Tasks.Task> örneğidir.</span><span class="sxs-lookup"><span data-stu-id="3a561-107">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="3a561-108">İstekler birden çok iş parçacığında eşzamanlı olarak yapıldığından, geçerli dizine erişim eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="3a561-108">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="3a561-109">Bu, öbek bölümlendirme bir örneğidir ve her bir öbek bir öğeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3a561-109">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="3a561-110">Tek seferde daha fazla öğe sağlayarak kilit üzerindeki çekişmeyi azaltabilir ve teorik olarak daha hızlı performans elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="3a561-110">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="3a561-111">Ancak, bazı bir noktada, tüm işler tamamlanana kadar tüm iş parçacıklarını meşgul tutmak için daha büyük parçalar ek yük dengeleme mantığını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="3a561-111">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a561-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a561-112">See also</span></span>

* [<span data-ttu-id="3a561-113">PLıNQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="3a561-113">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="3a561-114">Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama</span><span class="sxs-lookup"><span data-stu-id="3a561-114">How to: Implement a Partitioner for Static Partitioning</span></span>](how-to-implement-a-partitioner-for-static-partitioning.md)
