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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcb2fbf5e0a310156fdc6fac5fe736692e8ec133
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135347"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="f4525-102">Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma</span><span class="sxs-lookup"><span data-stu-id="f4525-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="f4525-103">Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Threading.SpinWait?displayProperty=nameWithType> aşamalı bir bekleme işlemini uygulamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="f4525-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="f4525-104">İlk aşamada, eşitleme nesnesi bir `Latch`, kilit kullanılabilir hale olup olmadığını denetlerken birkaç döngü için döner.</span><span class="sxs-lookup"><span data-stu-id="f4525-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="f4525-105">İkinci kısımda kilit kullanılabilir durumdaysa, ardından `Wait` yöntemi döndürür kullanmadan <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> beklemesi; gerçekleştirmek için Aksi takdirde, `Wait` bekleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f4525-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4525-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4525-106">Example</span></span>  
 <span data-ttu-id="f4525-107">Bu örnek çok basit bir uygulama bir Mandal eşitleme ilkel gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4525-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="f4525-108">Bekleme süresini çok kısa olması beklendiğinde bu veri yapısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4525-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="f4525-109">Bu örnek yalnızca gösterim amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="f4525-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="f4525-110">Tutma türü işlevselliği programınıza gerektirir kullanmayı <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f4525-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="f4525-111">Mandal kullanır <xref:System.Threading.SpinWait> yapılan sonraki çağrıda kadar yalnızca yerinde dönmeye nesne `SpinOnce` neden <xref:System.Threading.SpinWait> iş parçacığının zaman dilimi bekletilemiyor.</span><span class="sxs-lookup"><span data-stu-id="f4525-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="f4525-112">Bu noktada, Mandal çağırarak kendi içerik anahtarı neden <xref:System.Threading.WaitHandle.WaitOne%2A> üzerinde <xref:System.Threading.ManualResetEvent> ve zaman aşımı değerini geri kalanında geçirme.</span><span class="sxs-lookup"><span data-stu-id="f4525-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="f4525-113">Mandal ne sıklıkta kullanmadan kilit alınırken tarafından performansını artırabilirsiniz günlük çıktısını gösterir <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="f4525-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4525-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4525-114">See also</span></span>

- [<span data-ttu-id="f4525-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="f4525-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
- [<span data-ttu-id="f4525-116">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="f4525-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
