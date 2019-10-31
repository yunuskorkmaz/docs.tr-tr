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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137950"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="ca4a8-102">Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma</span><span class="sxs-lookup"><span data-stu-id="ca4a8-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="ca4a8-103">Aşağıdaki örnek, iki aşamalı bir bekleme işlemini uygulamak için bir <xref:System.Threading.SpinWait?displayProperty=nameWithType> nesnesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="ca4a8-104">İlk aşamada, eşitleme nesnesi `Latch`, kilidin kullanılabilir olup olmadığını denetlerken birkaç döngü için döner.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="ca4a8-105">İkinci aşamada, kilit kullanılabilir hale gelirse `Wait` yöntemi, bekleme işlemini gerçekleştirmek için <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> kullanılmadan döndürülür; Aksi takdirde, `Wait` bekleme işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca4a8-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca4a8-106">Example</span></span>  
 <span data-ttu-id="ca4a8-107">Bu örnek, bir mandal eşitleme temel öğesinin çok basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="ca4a8-108">Bu veri yapısını, bekleme sürelerinin çok kısa olması beklendiğinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="ca4a8-109">Bu örnek yalnızca tanıtım amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="ca4a8-110">Programınızda mandal türü işlevselliğe ihtiyacınız varsa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="ca4a8-111">Mandal, `SpinOnce` bir sonraki çağrıya <xref:System.Threading.SpinWait>, iş parçacığının zaman dilimini almasına neden olana kadar yerine geçmek için <xref:System.Threading.SpinWait> nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="ca4a8-112">Bu noktada, mandal, <xref:System.Threading.ManualResetEvent> <xref:System.Threading.WaitHandle.WaitOne%2A> çağırarak ve zaman aşımı değerinin geri kalanını geçirerek kendi bağlam anahtarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="ca4a8-113">Günlüğe kaydetme çıktısı, <xref:System.Threading.ManualResetEvent>kullanmadan kilidi alarak mandalın performansı ne sıklıkla artırabilmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4a8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca4a8-114">See also</span></span>

- [<span data-ttu-id="ca4a8-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="ca4a8-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)
- [<span data-ttu-id="ca4a8-116">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ca4a8-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
