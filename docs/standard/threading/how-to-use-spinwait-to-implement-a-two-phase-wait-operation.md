---
title: "Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma"
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
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="8e1bd-102">Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma</span><span class="sxs-lookup"><span data-stu-id="8e1bd-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="8e1bd-103">Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Threading.SpinWait?displayProperty=nameWithType> aşamalı bir bekleme işlemini uygulamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="8e1bd-104">İlk aşamada, eşitleme nesnesi bir `Latch`, kilit kullanılabilir hale olup olmadığını denetlerken birkaç döngüsü boyunca döner.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="8e1bd-105">İkinci aşamada kilit kullanılabilir hale gelirse sonra `Wait` yöntemi döndürür kullanmadan <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> kendi bekleyin; gerçekleştirmek için Aksi halde, `Wait` bekleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e1bd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e1bd-106">Example</span></span>  
 <span data-ttu-id="8e1bd-107">Bu örnek çok basit bir uygulama Mandal eşitleme ilkel gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="8e1bd-108">Bekleme süresini çok kısa olması beklenen olduğunda, bu veri yapısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="8e1bd-109">Bu örnek, yalnızca tanıtım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="8e1bd-110">Programınıza tutma türü işlevsellik gerektiriyorsa kullanmayı <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="8e1bd-111">Mandal kullanan <xref:System.Threading.SpinWait> sonraki çağrısı kadar yalnızca yerinde dönmeye nesne `SpinOnce` neden <xref:System.Threading.SpinWait> iş parçacığının zaman dilimi elde etmek üzere.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="8e1bd-112">Bu noktada, Mandal kendi içerik anahtarı çağırarak neden olan <xref:System.Threading.WaitHandle.WaitOne%2A> üzerinde <xref:System.Threading.ManualResetEvent> ve zaman aşımı değerini geri kalanı geçirme.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="8e1bd-113">Mandal ne sıklıkta kullanmadan kilit alınırken tarafından performansını artırabilirsiniz günlük çıktısı gösterir <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e1bd-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e1bd-114">See Also</span></span>  
 [<span data-ttu-id="8e1bd-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="8e1bd-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="8e1bd-116">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="8e1bd-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
