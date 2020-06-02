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
ms.openlocfilehash: 197e71cf4f00c98891e58e5f72974c0ec407e6ce
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288452"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="82eda-102">Nasıl yapılır: Dinamik Bölümleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="82eda-102">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="82eda-103">Aşağıdaki örnek, dinamik bölümlendirme uygulayan bir özel nasıl uygulanacağını <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> ve belirli aşırı yüklerden <xref:System.Threading.Tasks.Parallel.ForEach%2A> ve PLINQ 'ten nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="82eda-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82eda-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="82eda-104">Example</span></span>

<span data-ttu-id="82eda-105">Numaralandırıcı üzerinde bir bölüm çağırdığında <xref:System.Collections.IEnumerator.MoveNext%2A> , Numaralandırıcı bölüm bir liste öğesiyle birlikte sunulur.</span><span class="sxs-lookup"><span data-stu-id="82eda-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="82eda-106">PLıNQ ve durumunda <xref:System.Threading.Tasks.Parallel.ForEach%2A> , bölüm bir <xref:System.Threading.Tasks.Task> örneğidir.</span><span class="sxs-lookup"><span data-stu-id="82eda-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="82eda-107">İstekler birden çok iş parçacığında eşzamanlı olarak yapıldığından, geçerli dizine erişim eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="82eda-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="82eda-108">Bu, öbek bölümlendirme bir örneğidir ve her bir öbek bir öğeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="82eda-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="82eda-109">Tek seferde daha fazla öğe sağlayarak kilit üzerindeki çekişmeyi azaltabilir ve teorik olarak daha hızlı performans elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="82eda-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="82eda-110">Ancak, bazı bir noktada, tüm işler tamamlanana kadar tüm iş parçacıklarını meşgul tutmak için daha büyük parçalar ek yük dengeleme mantığını gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="82eda-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82eda-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82eda-111">See also</span></span>

* [<span data-ttu-id="82eda-112">PLıNQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="82eda-112">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="82eda-113">Nasıl yapılır: Statik Bölümleme için bir Bölümleyici Uygulama</span><span class="sxs-lookup"><span data-stu-id="82eda-113">How to: Implement a Partitioner for Static Partitioning</span></span>](how-to-implement-a-partitioner-for-static-partitioning.md)
