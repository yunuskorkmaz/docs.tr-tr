---
title: dangerousThreadingAPI MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b7c4e7f5612cb6a46f16b6e42327e8430d548e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="fc941-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="fc941-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="fc941-103">`dangerousThreadingAPI` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> yöntemi, geçerli iş parçacığı dışında bir iş parçacığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fc941-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fc941-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="fc941-104">Symptoms</span></span>  
 <span data-ttu-id="fc941-105">Bir uygulama yanıt vermiyor veya süresiz olarak askıda kalır.</span><span class="sxs-lookup"><span data-stu-id="fc941-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="fc941-106">Sistem veya uygulama verileri, geçici veya uygulamanın bile kapatıldı sonra öngörülemeyen durumda kalmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fc941-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="fc941-107">Beklendiği gibi bazı işlemler Tamamlanıyor değil.</span><span class="sxs-lookup"><span data-stu-id="fc941-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="fc941-108">Belirtiler yaygın olarak sorun için devralınan rastgele nedeniyle değişebilir.</span><span class="sxs-lookup"><span data-stu-id="fc941-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fc941-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="fc941-109">Cause</span></span>  
 <span data-ttu-id="fc941-110">Bir iş parçacığı başka bir iş parçacığı kullanarak zaman uyumsuz olarak askıya <xref:System.Threading.Thread.Suspend%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fc941-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="fc941-111">Bir işlem gerçekleştiriyor olabilir. başka bir iş parçacığı askıya almak güvenli olduğunda belirlemek için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="fc941-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="fc941-112">İş parçacığı askıya alma, veri bozulması veya invariants sonu neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc941-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="fc941-113">Bir iş parçacığı bir askıya alınır ve hiçbir zaman sürdürüldü kullanarak yerleştirilmelidir <xref:System.Threading.Thread.Resume%2A> yöntemi, uygulama süresiz olarak askıda ve büyük olasılıkla uygulama verileri zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="fc941-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="fc941-114">Bu yöntemleri geçersiz olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="fc941-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="fc941-115">Eşitleme temelleri hedef iş parçacığı tarafından tutuluyor bunlar sırasında askıya tutulan kalır.</span><span class="sxs-lookup"><span data-stu-id="fc941-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="fc941-116">Bu başka bir iş parçacığı, örneğin iş parçacığı gerçekleştirme kilitlenmeye neden olabilir <xref:System.Threading.Thread.Suspend%2A>, basit bir Kilitle girişimi.</span><span class="sxs-lookup"><span data-stu-id="fc941-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="fc941-117">Bu durumda, sorunun bir kilitlenme ortaya çıkmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc941-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fc941-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="fc941-118">Resolution</span></span>  
 <span data-ttu-id="fc941-119">Kullanılmasını tasarımları kaçının <xref:System.Threading.Thread.Suspend%2A> ve <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc941-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="fc941-120">Eşitleme temelleri iş parçacıkları arasında işbirliği için gibi kullandığınız <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, veya C# `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fc941-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="fc941-121">Bu yöntemleri kullanmanız gerekiyorsa olan zaman penceresini azaltmak ve iş parçacığı askıya alınmış durumdayken, yürütülen kod miktarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="fc941-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fc941-122">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="fc941-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="fc941-123">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fc941-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="fc941-124">Yalnızca veri tehlikeli iş parçacığı oluşturma işlemleri hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="fc941-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fc941-125">Çıkış</span><span class="sxs-lookup"><span data-stu-id="fc941-125">Output</span></span>  
 <span data-ttu-id="fc941-126">MDA etkinleştirilmesi neden tehlikeli iş parçacığı yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fc941-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fc941-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc941-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="fc941-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc941-128">Example</span></span>  
 <span data-ttu-id="fc941-129">Aşağıdaki kod örneğinde yapılan bir çağrı gösterilmektedir <xref:System.Threading.Thread.Suspend%2A> etkinleştirmeyi neden yöntemi `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="fc941-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```  
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc941-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc941-130">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="fc941-131">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="fc941-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="fc941-132">lock Deyimi</span><span class="sxs-lookup"><span data-stu-id="fc941-132">lock Statement</span></span>](~/docs/csharp/language-reference/keywords/lock-statement.md)
