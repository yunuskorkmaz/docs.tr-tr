---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e83505a36252457d286bc7fbc6bbe442732229a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="spinlock"></a><span data-ttu-id="f2ef5-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="f2ef5-102">SpinLock</span></span>
<span data-ttu-id="f2ef5-103"><xref:System.Threading.SpinLock> Bir kilidi beklerken dönerek bir alt düzey, karşılıklı dışlama eşitleme ilkel yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="f2ef5-104">Bekleme süresini kısa ve çakışma en az olduğunda olması beklenen zaman çok çekirdekli bilgisayarlarda <xref:System.Threading.SpinLock> kilitleri diğer tür daha iyi gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="f2ef5-105">Ancak, kullanmanızı öneririz <xref:System.Threading.SpinLock> yalnızca zaman, profil oluşturma saptamanıza <xref:System.Threading.Monitor?displayProperty=nameWithType> yöntemi veya <xref:System.Threading.Interlocked> yöntemleri önemli ölçüde performans programınızın yavaşlamasının.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="f2ef5-106"><xref:System.Threading.SpinLock>Bunu henüz kilidi ele geçirmiş değil olsa bile iş parçacığının zaman dilimi verim.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="f2ef5-107">İş parçacığı önceliği ters çevirmeyi önlemek için ve ilerleme atık toplayıcı etkinleştirmek için bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="f2ef5-108">Kullandığınızda, bir <xref:System.Threading.SpinLock>, birden çok çok kısa bir süre için hiçbir iş parçacığı kilidi tutabilir ve kilidi tutan sırada hiçbir iş parçacığı engelleyebilirsiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="f2ef5-109">SpinLock bir değer türü olduğundan, aynı kilit başvurmak için iki kopya düşünüyorsanız açıkça başvuruya göre geçirdiğiniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="f2ef5-110">Bu tür kullanma hakkında daha fazla bilgi için bkz: <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f2ef5-111">Bir örnek için bkz: [nasıl yapılır: alt düzey eşitleme için SpinLock kullanma](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="f2ef5-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="f2ef5-112"><xref:System.Threading.SpinLock>destekleyen bir *iş parçacığı*-*izleme* geliştirme aşaması boyunca belirli bir zamanda kilit iş parçacığı izlemenize yardımcı olması için kullanabileceğiniz modu.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="f2ef5-113">İş parçacığı izleme modunu hata ayıklama için faydalıdır, ancak performans azaltabileceğinden, programınızın yayın sürümünü kapatmak olmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="f2ef5-114">Daha fazla bilgi için bkz: [nasıl yapılır: spinlock'ta etkinleştirmek iş parçacığı izleme modunu](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span><span class="sxs-lookup"><span data-stu-id="f2ef5-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ef5-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2ef5-115">See Also</span></span>  
 [<span data-ttu-id="f2ef5-116">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="f2ef5-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
