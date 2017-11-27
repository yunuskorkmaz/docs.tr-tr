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
ms.openlocfilehash: a84fd957800f0cedcd92b36929721b4d0d51b7fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="9c52a-102">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="9c52a-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="9c52a-103">`dangerousThreadingAPI` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> yöntemi, geçerli iş parçacığı dışında bir iş parçacığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9c52a-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9c52a-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="9c52a-104">Symptoms</span></span>  
 <span data-ttu-id="9c52a-105">Bir uygulama yanıt vermiyor veya süresiz olarak askıda kalır.</span><span class="sxs-lookup"><span data-stu-id="9c52a-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="9c52a-106">Sistem veya uygulama verileri, geçici veya uygulamanın bile kapatıldı sonra öngörülemeyen durumda kalmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9c52a-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="9c52a-107">Beklendiği gibi bazı işlemler Tamamlanıyor değil.</span><span class="sxs-lookup"><span data-stu-id="9c52a-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="9c52a-108">Belirtiler yaygın olarak sorun için devralınan rastgele nedeniyle değişebilir.</span><span class="sxs-lookup"><span data-stu-id="9c52a-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9c52a-109">Sebep</span><span class="sxs-lookup"><span data-stu-id="9c52a-109">Cause</span></span>  
 <span data-ttu-id="9c52a-110">Bir iş parçacığı başka bir iş parçacığı kullanarak zaman uyumsuz olarak askıya <xref:System.Threading.Thread.Suspend%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9c52a-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="9c52a-111">Bir işlem gerçekleştiriyor olabilir. başka bir iş parçacığı askıya almak güvenli olduğunda belirlemek için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="9c52a-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="9c52a-112">İş parçacığı askıya alma, veri bozulması veya invariants sonu neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c52a-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="9c52a-113">Bir iş parçacığı bir askıya alınır ve hiçbir zaman sürdürüldü kullanarak yerleştirilmelidir <xref:System.Threading.Thread.Resume%2A> yöntemi, uygulama süresiz olarak askıda ve büyük olasılıkla uygulama verileri zarar verebilir.</span><span class="sxs-lookup"><span data-stu-id="9c52a-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="9c52a-114">Bu yöntemleri geçersiz olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="9c52a-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="9c52a-115">Eşitleme temelleri hedef iş parçacığı tarafından tutuluyor bunlar sırasında askıya tutulan kalır.</span><span class="sxs-lookup"><span data-stu-id="9c52a-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="9c52a-116">Bu başka bir iş parçacığı, örneğin iş parçacığı gerçekleştirme kilitlenmeye neden olabilir <xref:System.Threading.Thread.Suspend%2A>, basit bir Kilitle girişimi.</span><span class="sxs-lookup"><span data-stu-id="9c52a-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="9c52a-117">Bu durumda, sorunun bir kilitlenme ortaya çıkmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c52a-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9c52a-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="9c52a-118">Resolution</span></span>  
 <span data-ttu-id="9c52a-119">Kullanılmasını tasarımları kaçının <xref:System.Threading.Thread.Suspend%2A> ve <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c52a-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="9c52a-120">Eşitleme temelleri iş parçacıkları arasında işbirliği için gibi kullandığınız <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, veya C# `lock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="9c52a-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="9c52a-121">Bu yöntemleri kullanmanız gerekiyorsa olan zaman penceresini azaltmak ve iş parçacığı askıya alınmış durumdayken, yürütülen kod miktarını en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="9c52a-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9c52a-122">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="9c52a-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="9c52a-123">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9c52a-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="9c52a-124">Yalnızca veri tehlikeli iş parçacığı oluşturma işlemleri hakkında raporlar.</span><span class="sxs-lookup"><span data-stu-id="9c52a-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9c52a-125">Çıkış</span><span class="sxs-lookup"><span data-stu-id="9c52a-125">Output</span></span>  
 <span data-ttu-id="9c52a-126">MDA etkinleştirilmesi neden tehlikeli iş parçacığı yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9c52a-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9c52a-127">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9c52a-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="9c52a-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c52a-128">Example</span></span>  
 <span data-ttu-id="9c52a-129">Aşağıdaki kod örneğinde yapılan bir çağrı gösterilmektedir <xref:System.Threading.Thread.Suspend%2A> etkinleştirmeyi neden yöntemi `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="9c52a-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c52a-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c52a-130">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="9c52a-131">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="9c52a-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="9c52a-132">lock deyimi</span><span class="sxs-lookup"><span data-stu-id="9c52a-132">lock Statement</span></span>](~/docs/csharp/language-reference/keywords/lock-statement.md)
