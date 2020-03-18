---
title: 'Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 5bac174660177fd47e1f345e64581e35ae4c0ffc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137950"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="1da10-102">Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma</span><span class="sxs-lookup"><span data-stu-id="1da10-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="1da10-103">Aşağıdaki örnek, iki aşamalı <xref:System.Threading.SpinWait?displayProperty=nameWithType> bir bekleme işlemi uygulamak için bir nesnenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1da10-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="1da10-104">İlk aşamada, eşitleme nesnesi, `Latch`bir , kilit kullanılabilir hale gelip gelmediğini denetler ken birkaç döngü için döner.</span><span class="sxs-lookup"><span data-stu-id="1da10-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="1da10-105">İkinci aşamada, kilit kullanılabilir hale gelirse, `Wait` o zaman <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> yöntemi bekleme gerçekleştirmek için kullanmadan döndürür; aksi `Wait` takdirde, bekleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1da10-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1da10-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1da10-106">Example</span></span>  
 <span data-ttu-id="1da10-107">Bu örnek, bir Mandal eşitleme ilkel çok temel bir uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="1da10-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="1da10-108">Bekleme sürelerinin çok kısa olması beklenirken bu veri yapısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1da10-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="1da10-109">Bu örnek yalnızca gösteri amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="1da10-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="1da10-110">Programınızda mandal türü işlevselliği gerekiyorsa, 'yi kullanmayı <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>düşünün.</span><span class="sxs-lookup"><span data-stu-id="1da10-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="1da10-111">Mandal, <xref:System.Threading.SpinWait> iş parçacığının zaman dilimini `SpinOnce` verim <xref:System.Threading.SpinWait> almasına neden olmak için nesneyi yalnızca bir sonraki çağrıya kadar yerinde döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1da10-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="1da10-112">Bu noktada, mandal, zaman atlama <xref:System.Threading.WaitHandle.WaitOne%2A> değerinin <xref:System.Threading.ManualResetEvent> geri kalanını çağırArak ve geçirerek kendi bağlam anahtarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1da10-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="1da10-113">Günlüğe kaydetme çıktısı, Mandal'ın kilidi kullanmadan kilidi <xref:System.Threading.ManualResetEvent>edinerek performansı ne sıklıkta artırabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1da10-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da10-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1da10-114">See also</span></span>

- [<span data-ttu-id="1da10-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="1da10-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)
- [<span data-ttu-id="1da10-116">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="1da10-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
