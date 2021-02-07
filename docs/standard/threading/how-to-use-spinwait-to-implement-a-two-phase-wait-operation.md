---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Two-Phase bir bekleme Işlemi uygulamak için SpinWait kullanma'
title: 'Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 95ff74d328bcfa9f76d2cac017e5520b6d1375b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666699"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="f3597-103">Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma</span><span class="sxs-lookup"><span data-stu-id="f3597-103">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>

<span data-ttu-id="f3597-104">Aşağıdaki örnek, bir <xref:System.Threading.SpinWait?displayProperty=nameWithType> nesnenin iki aşamalı bir bekleme işlemini uygulamak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3597-104">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="f3597-105">İlk aşamada, eşitleme nesnesi a, `Latch` kilidin kullanılabilir olup olmadığını kontrol ederken birkaç döngü için döner.</span><span class="sxs-lookup"><span data-stu-id="f3597-105">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="f3597-106">İkinci aşamada, kilit kullanılabilir hale gelirse, `Wait` yöntemi <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> beklemeyi gerçekleştirmek için kullanılmadan döner; Aksi takdirde, `Wait` beklemeyi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f3597-106">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3597-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3597-107">Example</span></span>  

 <span data-ttu-id="f3597-108">Bu örnek, bir mandal eşitleme temel öğesinin çok basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3597-108">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="f3597-109">Bu veri yapısını, bekleme sürelerinin çok kısa olması beklendiğinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f3597-109">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="f3597-110">Bu örnek yalnızca tanıtım amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="f3597-110">This example is for demonstration purposes only.</span></span> <span data-ttu-id="f3597-111">Programınızda mandal türü işlevselliğe ihtiyacınız varsa kullanmayı göz önünde bulundurun <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f3597-111">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="f3597-112">Mandal, <xref:System.Threading.SpinWait> yalnızca bir sonraki çağrıya, `SpinOnce` <xref:System.Threading.SpinWait> iş parçacığının zaman dilimini vermesine neden olana kadar yerine dönmesi için nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3597-112">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="f3597-113">Bu noktada, mandal, <xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.ManualResetEvent> zaman aşımı değerinin geri kalanını geçirerek ve ' ı çağırarak kendi bağlam anahtarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f3597-113">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="f3597-114">Günlüğe kaydetme çıktısı, ' i kullanmadan kilidi alarak mandalın performansı ne sıklıkta artırabiltiğini gösterir <xref:System.Threading.ManualResetEvent> .</span><span class="sxs-lookup"><span data-stu-id="f3597-114">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3597-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3597-115">See also</span></span>

- [<span data-ttu-id="f3597-116">SpinWait</span><span class="sxs-lookup"><span data-stu-id="f3597-116">SpinWait</span></span>](spinwait.md)
- [<span data-ttu-id="f3597-117">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="f3597-117">Threading Objects and Features</span></span>](threading-objects-and-features.md)
